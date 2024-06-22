# Descrição do Pattern (não necessariamente ligado ao POO)

Basicamente, a ideia do Singleton é de gerenciar uma única instância de um código
sem que existam outras instâncias do mesmo.

Ele é uma forma de controlar o acesso concorrente de um recurso que é compartilhado, 
mas onde só pode ter **UMA INSTÂNCIA**. Esse último passo em muitos casos pode ser quebrado
pela má utilização do _Pattern_

Frequentemente é referido como um _Anti-Pattern_ por diversas razões, mas principalmente
por conta do estado global que pode ser mudado em diversos pontos de uma aplicação,
o que pode causar comportamentos inesperados. 

Não significa que não deva ser usado, mas pode facilmente ser implementado de forma errada, 
e utilizado para resolver um problema que não é totalmente resolvido por ele.

- Um possível mal exemplo: 

    Imagine um dev chamado Cleitinho que está fazendo uma aplicação que usa uma conexão com banco
    de dados. Ao criar uma conexão ele cria um método que adquire a conexão, realiza a query, e 
    depois fecha a conexão. Agora imagine que Cleitinho esqueceu que antes de executar a query,
    é preciso processar um valor que é produto de outra query e será usado na query descrita anteriormente.
    Só que ele não percebe que ao processar um valor vindo da outra query, significa que a conexão tentará
    ser adquirida novamente e será fechada precocemente, e quando o valor processado ser utilizado na 
    query anteriormente descrita e esta ser rodada, é possível que o erro de que a conexão foi fechada
    seja lançado.

- Agora um possível bom exemplo:

    Códigos de configurações globais e constantes, ou o mais comum, um Singleton para os logs do sistema, 
    o Logger que como não altera o funcionamento da aplicação, não compartilha os riscos do estado global. Além disso o logger geralmente é global e com certeza não terá mais de um, e deve ser utilizado em 
    majoritariamente em todas as partes de uma aplicação. 