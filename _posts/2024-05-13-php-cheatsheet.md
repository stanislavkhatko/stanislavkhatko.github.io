---
layout: post
title: PHP cheatsheet
date: 2024-05-13 20:32:00
description: Most used and useful PHP functions and methods.
tags: [ 'php', 'code' ]
categories: [ 'code']
featured: true
---

List of useful PHP.

Exit the file, string inside get's echo'ed
```php
die("This file is not ment to be ran. ¯\_(ツ)_/¯");
exit("This file is not ment to be ran. ¯\_(ツ)_/¯");
```


Printing
```php
echo ""; // Print a string or type that can be made into a string(I.E int, float).
print_r($arr); // Print anything, with type hints for array's and object's
var_dump($arr); // Print anything, with type hints for any value and sizes
```

Usefull string manipulation methods
```php
$string = 'Awesome cheatsheets';

str_contains($string, 'cheat'); // Find if the string contains the specified string (PHP >= 8.0)
str_replace('Awesome', 'Bonjour', $string); // Replace all occurence
strcmp($string, 'Awesome cheatsheets'); // Compare two strings
strpos($string, 'a', 0); // Get position in the string
str_split($string, 2); // Split the string
strrev($string); // Reverse a string
trim($string); // Strip whitespace from the beginning and end of a string
ucfirst($string); // Make a string's first character uppercase
lcfirst($string); // Make a string's first character lowercase
substr($string, 0, 4); // Return part of a string
```

### Declaring an Array

Indexed Array
```php
$arr = array("John", "Doe", "Lorem", "Ipsum");
```

Associative Array
```php
$arr = array("John"=>"10", "Doe"=>"200", "Doe"=>"3000", "Ipsum"=>"40000");
```

Multidimensional Arrays
```php
$arr = array (
    array("John",100,180),
    array("Doe",150,130),
    array("Lorem",500,200),
    array("Ipsum",170,150)
);
```

Declaring array with short syntax
```php
$arr = ["John", "Doe", "Lorem", "Ipsum"]; // Indexed Array
$arr = ["John"=>"10", "Doe"=>"200", "Doe"=>"3000", "Ipsum"=>"40000"]; // Associative Array
$arr = [
    ["John",100,180],
    ["Doe",150,130],
    ["Lorem",500,200],
    ["Ipsum",170,150], // You can have a "," at the end without throwing syntax errors
];
```

Sorting an Array
```php
sort($arr); // Sort arrays in ascending order.
rsort($arr); // Sort arrays in descending order.
asort($arr); // Sort associative arrays in ascending order, according to the value.
ksort($arr); // Sort associative arrays in ascending order, according to the key.
arsort($arr); // Sort associative arrays in descending order, according to the value.
krsort($arr); // Sort associative arrays in descending order, according to the key.
```

### Conditions
If/Elseif/Else
```php
if($i > 10) {

} elseif( $i > 100) {

} else {

}
```

Ternary
```php
$string = $state == 'Running' ? 'He is running' : 'I don\'t know';
```

Null coalescing
```php
$string = $startDate ?? '';
```


Ways of looping
```php
continue; // Skip current iter
break; // Exit loop
```

Foreach
```php
foreach($arr as $key => $value) {
    $key = $key;
    $value = $value;
}
```

For
```php
for($i = 0; $i < count($arr); $i++) {
    $key = $i;
    $value = $arr[$i];
}
```

While
```php
$i = 0;
while($i < count($arr) - 1) {
    $key = $i;
    $value = $arr[$i];
}
```

Do while
```php
$i = 0;
do {
    $key = $i;
    $value = $arr[$i];
} while($i < count($arr));
```

Switch
```php
switch($arr) {
    case 1:
        break;
    case 2:
        break;
    case 3:
        break;
    default:
}
```

### Global variables
```php
$_SERVER; // SERVER variables
$_GET; // Query params
$_POST; // Post fields
$_REQUEST; // GET and POST together
$GLOBALS; // Array of global variables
$_SESSION; // Browser session
$_FILES; // Array of files that are sent in request
$_COOKIE; // Array of cookies sent in request
$_ENV; // php.ini options
$argv; // Array of terminal arguments (filename included)
$argc; // Number of arguments passed into terminal
```

### Functions
```php

 // Simple function
 function name($parameter);

 // Function with return type (void, int, float, string, array, object, mixed)
 function name($parameter) : void;

 // Function with optionnal parameter
 function name($parameter = '') : string;

 // Function with typed parameter (? means "can be null")
 function name(?string $parameter) : ?string;

 // Function with union types (PHP >= 8.0)
 function name(int|string $parameter1, array $parameter2) : int|string;

 // Function call
 name('my_parameter');

 // Null safe operator (PHP >= 8.0)
 $myObject?->getName()?->startWith('A');
```

### Class 
```php
class NormalClass extends AbstractClassName implements InterfaceName
{

    use TraitName;

    // --> PROPERTY TYPES <--

    /**
     * Public property, everyone can access this property. 
     * @var Type
     */
    public $property;

    /**
     * Private property, only this instance can access this property.
     * @var Type
     */
    private $property;

    /**
     * Protected property, this instance and childs can access this property.
     * @var Type
     */
    protected $property;

    /**
     * Static property, is the same for all instances of this class.
     * @var Type
     */
    static $property;

    // --> FUNCTION TYPES <--

    /**
     * Public function, everyone can access this function.
     * @param Type
     * @return Type
     */
    public function publicFunction(Type $var = null): Type
    {
    }

    /**
     * Private function, only this instance can access this function.
     * @param Type
     * @return Type
     */
    private function privateFunction(Type $var = null): Type
    {
    }

    /**
     * Protected function, this instance and childs can access this function.
     * @param Type
     * @return Type
     */
    protected function protectedFunction(Type $var = null): Type
    {
    }
    
    /**
     * Static function, doesn't need an instance to be executed.
     * @param Type
     * @return Type
     */
    public static function staticFunction(Type $var = null): Type
    {
    }

    // --> MAGIC METHODS <--

    /**
     * Gets triggered on creating a new class instance
     * http://php.net/manual/en/language.oop5.decon.php
     * @param Type
     * @return void
     */
    public function __construct(Type $var = null)
    {
    }

    /**
     * Gets triggered on destruction of a class instance
     * http://php.net/manual/en/language.oop5.decon.php
     * @return void
     */
    public function __destruct()
    {
    }

    /**
     * __set() is run when writing data to inaccessible properties.
     * http://php.net/manual/en/language.oop5.overloading.php
     * @param string name
     * @param mixed value
     * @return void
     */
    public function __set(string $name , mixed $value)
    {
    }

    /**
     * __get() is utilized for reading data from inaccessible properties.
     * http://php.net/manual/en/language.oop5.overloading.php
     * @param string name
     * @return mixed
     */
    public function __get(string $name)
    {
    }

    /**
     * __isset() is triggered by calling isset() or empty() on inaccessible properties.
     * http://php.net/manual/en/language.oop5.overloading.php
     * @param string name
     * @return bool
     */
    public function __isset(string $name)
    {
    }

    /**
     * __unset() is invoked when unset() is used on inaccessible properties.
     * http://php.net/manual/en/language.oop5.overloading.php
     * @param string name
     * @return void
     */
    public function __unset(string $name)
    {
    }

    /**
     * __call is triggered when invoking inaccessible methods in an object context.
     * http://php.net/manual/en/language.oop5.overloading.php
     * @param string name
     * @param array arguments
     * @return mixed
     */
    public function __call(string $name, array $arguments)
    {
    }

    /**
     * __callStatic() is triggered when invoking inaccessible methods in a static context.
     * http://php.net/manual/en/language.oop5.overloading.php
     * @param string name
     * @param array arguments
     * @return mixed
     */
    public static function __callStatic(string $name, array $arguments)
    {
    }

    /**
     * http://php.net/manual/en/language.oop5.magic.php
     * @return array
     */
    public function __sleep()
    {
    }

    /**
     * http://php.net/manual/en/language.oop5.magic.php
     * @return void
     */
    public function __wakeup()
    {
    }

    /**
     * http://php.net/manual/en/language.oop5.magic.php
     * @return string
     */
    public function __toString()
    {
    }

    /**
     * http://php.net/manual/en/language.oop5.magic.php
     * @param Type
     * @return mixed
     */
    public function __invoke(Type $var = null)
    {
    }

    /**
     * http://php.net/manual/en/language.oop5.magic.php
     * @param array properties
     * @return object
     */
    public static function __set_state(array $properties)
    {
    }

    /**
     * http://php.net/manual/en/language.oop5.magic.php
     * @return array
     */
    public function __debugInfo()
    {
    }

}
```

Every class that has implemented this interface need to have the same functions.
```php
interface InterfaceName
{

    public function FunctionName(Type $var = null): Type;

}
```

Combination of class and interface.
```php
abstract class AbstractClassName
{

    /**
     * Classes extending this abstract class need to have this function.
     * @param Type
     * @return Type
     */
    abstract function abstractFunction(Type $var = null): Type;
}
```


Basic Implementation of LoggerAwareInterface.
```php
trait LoggerAwareTrait
{
    /**
     * The logger instance.
     *
     * @var LoggerInterface
     */
    protected $logger;
    /**
     * Sets a logger.
     *
     * @param LoggerInterface $logger
     */
    public function setLogger(LoggerInterface $logger)
    {
        $this->logger = $logger;
    }
}
```


Example with use of LoggerAwareTrait.
```php
class ClassWithLogger
{
    /**
     * Use the LoggerAwareTrait in this class.
     */
    use LoggerAwareTrait;
}
```

Originated from [github](https://github.com/LeCoupa/awesome-cheatsheets)
