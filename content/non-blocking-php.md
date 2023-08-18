# PHP assíncrono (não-bloqueante)

Antes vamos entender o que é **assíncrono**. Tem alguma ideia?

Pela etimologia da palavra: assíncrono é tudo aquilo que **não** é síncrono.<br>
Parece besta, mas *assíncrono* é a palavra "síncrono" com o prefixo de negação "a", logo, a definição de **assíncrono** é: tudo aquilo que não é síncrono.

## Ok, então o que é síncrono?

Síncrono é aquilo que respeita uma sequência, uma coisa após a outra, uma etapa espera outra etapa.<br>
**Logo,** assíncrono é o que não, necesserariamente, respeita essa ordem de etapas sequenciais.

## Por que assíncrono é bom?

Você deve estar se perguntando: por que não respeitar uma sequência de etapas é algo bom?

Gosto muito da analogia do garçom num restaurante:

Imagina que as etapas de um garçom sejam:
1. Levar os clientes até a mesa
2. Anotar os pedidos
3. Buscar os pedidos da cozinha e levar até a mesa

Simples, certo?

Isso funciona muito bem quando você pensa no garçom atendendo 1 único cliente.

Agora imagina como seria se chegassem mais pessoas no restaurante, imagina ter que esperar o garçom atender um cliente primeiro:
- Esperar o cliente escolher um prato do cardápio
- Esperar a cozinha preparar o prato
- Esperar o cliente terminar de comer
- etc

**Você ia ficar de pé, na porta do restaurante, olhando o garçom esperar tudo isso acontecer pra depois iniciar uma nova sequência de etapas com você?**

Seria estranho, não é mesmo? **Mas é isso que acontece no PHP** 😮

O PHP é tradicionalmente síncrono, cada processo/worker do PHP-FPM lida com apenas uma requisição por vez e cada I/O (chamadas ao banco de dados, por exemplo) que você faz também **bloqueia** todo esse processo.

## Por isso a ideia de PHP assíncrono!

Com o PHP assíncrono a gente pode quebrar essa barreira e fazer as aplicações PHP terem **I/O não-bloqueante**, e se o processo não bloqueia, isso significa que você pode atender várias requisições simultaneamente nesse mesmo processo, aumentando consideravelmente a eficiência dos recursos utilizados no servidor.
