
### Geral

As regras são baseadas no PSR-2. Não havendo algo relacionado aqui deve-se respeitar o que consta na [PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md)

- Arquivos **DEVEM** usar apenas <?php 

- Todos os arquivos devem ser salvos na codificação **UTF-8**. Configurar editores e IDEs usadas para salvar desta forma.

- Todos os arquivos PHP **DEVEM** terminar com uma linha em branco

- A tag de fechamento "?>" **DEVE** ser omitida em arquivos que contém apenas código PHP

- Nomes de classes **DEVEM** ser declaradas no formato StudlyCaps.  Exemplo: RestController

- Cada classe **DEVE** estar em um arquivo separado e **DEVE** existir uma declaração de namespace

- Constantes de classe **DEVEM** ser declaradas em maiúsculas e com underscore como separador. Exemplo: PAYMENT_TYPE

- Nomes de métodos **DEVEM** ser declarados em camelCase. Exemplo: getPaymentMode

- Código **DEVE** usar 4 espaços para indentação e não tabs

- Linhas **PREFERENCIALMENTE** precisam ter 80 caracteres ou menos

- Em métodos onde o retorno é opcional (void)  **PREFERENCIALMENTE**  retornar o ponteiro do próprio objeto ($this)

- **DEVE** ter uma linha em branco depois da declaração do namespace e **DEVE** ter uma linha em branco depois do bloco de declaração dos uses

- DEVE existir apenas um use por declaração. Exemplo correto:

```php
use Core\Service\ParameterFactory;
use Core\Service\ParameterSet;
use Core\Service\Service;
```

Exemplo ERRADO:

```php
use Core\Service\ParameterFactory,
    Core\Service\ParameterSet,
	Core\Service\Service;
```

- As declarações de use **DEVEM** vir após a declaração da namespace

- As chaves de abertura e fechamento da classe **DEVEM** ser em novas linhas. Exemplo:

```php
class Auth extends Service
{
	//código
}
```

- As chaves de abertura e fechamento de métodos **DEVEM** ser em novas linhas. Exemplo:

```php
public function authenticate(ParameterSet $params)
{   
	//código
}
```

- A visibilidade (public, private, protected) **DEVE** ser declarada em todos os métodos e propriedades. abstract e final DEVEM ser declaradas antes da visibilidade. static **DEVE** ser declarado depois da visibilidade.

- Variáveis **NÃO DEVEM** iniciar com underscore como forma de definição de visibilidade.

- As chaves de abertura de estruturas de controle **DEVEM** ser na mesma linha, as de fechamento **DEVEM** ser em nova linha. Parênteses de abertura de estruturas de controle **NÃO DEVE** ter espaços depois e o de fechamento **NÃO DEVE** ter espaços antes.

Exemplo:

```php
if (count($user) == 0) {
    throw new Exception("Login ou senha inválidos");
}
```

- Palavras chave do PHP **DEVEM** ser em minúsculas. O mesmo para true, false, null.

- As palavras chave extends e implements **DEVEM** ser declaradas na mesma linha do nome da classe. Exemplo:

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

- Nomes de variáveis **DEVEM** conter somente caracteres alfanuméricos, não sendo underscores permitidos. Números são permitidos mas são desencorajados na maioria dos casos.

- Nomes de variáveis, métodos e classes **DEVEM** ser em inglês. Exemplos:

```php
$filter = $this->getFilter();
$client = $this->getClient();
```

- A utilização de verbos é encorajada, ou seja, variáveis e métodos **DEVEM** sempre ser tão verbais quanto prático para descrever os dados que o desenvolvedor pretende armazenar nelas. Nomes concisos de variáveis como "$i" e "$n" são desencorajados para todos os contextos de laço, exceto os menores. Se um loop contém mais de 20 linhas de código então as variáveis de índice **devem** ter nomes mais descritivos.

- Nomes de funções **DEVEM** conter somente caracteres alfanuméricos, não sendo underscores permitidos. Números são permitidos mas desencorajados na maioria dos casos.

- A declaração de um método **DEVEM** se parecer com o exemplo abaixo. Note a localização dos parênteses, espaços e chaves:

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

- Na lista de argumentos de um método **NÃO DEVE** existir espaços antes de cada vírgula e **DEVEM** existir um espaço após cada vírgula.

# Estruturas de controle

Nos exemplos a seguir observar a posição de espaços, vírgulas e parênteses. 

## if, elseif, else

```php
<?php

if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```

## switch, case

```php
<?php

switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```

## while, do while

```php
<?php

while ($expr) {
    // structure body
}

<?php

do {
    // structure body;
} while ($expr);
```

## for

```php
<?php

for ($i = 0; $i < 10; $i++) {
    // for body
}
```

## foreach

```php
<?php

foreach ($iterable as $key => $value) {
    // foreach body
}
```

## try, catch

```php
<?php

try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
}
```

## Comentários gerais

Trechos de código complexos devem ser documentados, podendo-se usar comentários de uma linha (``//``) ou de múltiplas linhas (``/*`` e ``*/``)

## PHP Code Sniffer

Para analisar o estilo de programação é possível usar o comando como no exemplo abaixo:

	./vendor/bin/phpcs -p --standard=PSR2 --runtime-set ignore_errors_on_exit 1 --runtime-set ignore_warnings_on_exit 1 module/Api/src/

Também é possível configurar as IDEs de desenvolvimento para fazer isso automaticamente, como o Eclipse e o [PhpStorm](https://confluence.jetbrains.com/display/PhpStorm/PHP+Code+Sniffer+in+PhpStorm#PHPCodeSnifferinPhpStorm-InstallingviaComposer)

O phpcs pode ser incluído no processo de pre-commit, então ele será executado durante o fluxo normal de desenvolvimento. [Saiba mais](https://github.com/intaro/php-git-hooks).

Quando for fazer um commit, caso ele falhe e você receba uma mensagem como: 

### Example of output

```bash
$ git ci -m "commit message"
Intaro Code Quality Tool
Fetching files
Running PHPLint
Checking code style
1) src/Acme/DemoBundle/Tests/Controller/DefaultControllerTest.php (unused_use, eof_ending)

  [Exception]
  There are coding standards violations!
```

```bash
$ git ci -m "commit message"
Intaro Code Quality Tool
Fetching files
Running PHPLint
Checking code style
Checking code style with PHPCS
FILE: ...m/src/Acme/DemoBundle/Tests/Controller/DefaultControllerTest.php
--------------------------------------------------------------------------------
FOUND 0 ERROR(S) AND 2 WARNING(S) AFFECTING 2 LINE(S)
--------------------------------------------------------------------------------
 197 | WARNING | Line exceeds 120 characters; contains 172 characters
 212 | WARNING | Line exceeds 120 characters; contains 128 characters
--------------------------------------------------------------------------------

  [Exception]
  There are PHPCS coding standards violations!
```

Você deverá seguir a instrução acima e corrigir o erro reportado. Depois que os erros reportados forem corrigidos você pode tentar o commit novamente e ele funcionará.

## Suporte ao PHP 7

Deve-se utilizar sempre que possível o support a type hinting e return types adicionado no PHP 7:

```php
public function getToken(): string
{
    return $this->token;
}

public function setToken(string $token)
{
    $this->token = $token;
}
```

### Referências

[Dicas do livro Clean Code: Handbook of Agile Software Craftmanship](http://www.jeancarlomachado.com.br/post/visualizar/00053/dicas-do-livro-clean-code-handbook-of-agile-software-craftmanship)

[PHP The Right Way](http://www.phptherightway.com/)

[Coderockr](https://github.com/Coderockr/Standards)
