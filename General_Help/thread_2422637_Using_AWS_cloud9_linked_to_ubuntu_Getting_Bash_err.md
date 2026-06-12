---
title: "Using AWS cloud9 linked to ubuntu Getting Bash error while running PHP"
date: 2019-07-11
forum: General Help
---

### Post by aruneshdutta on 2019-07-11
I just began using c9 tried running following php code with runner PHP-CLI getting bash error

running sample code :: [https://docs.aws.amazon.com/cloud9/latest/user-guide/sample-php.html](https://docs.aws.amazon.com/cloud9/latest/user-guide/sample-php.html)


(standard_in) 1: syntax error
bash: line 9: [: -eq: unary operator expected
Kindly guide how to fix
[INDENT]<?php[/INDENT][INDENT]print(&#8216;Hello, World!&#8217;);
print("\nThe sum of 2 and 3 is 5.");
$sum = (int)$argv[1] + (int)$argv[2];
print("\nThe sum of $argv[1] and $argv[2] is $sum.");
?>


[/INDENT]

---

### Post by Holger_Gehrke on 2019-07-11
You've got backticks instead of single quotes around the string "Hello, World". The backticks make php call the shell to execute whatever is between the backticks.

Holger

---

### Post by aruneshdutta on 2019-07-14
I am trying to simply run the following code after removing hello world just to try as guided in [https://docs.aws.amazon.com/cloud9/latest/user-guide/sample-php.html](https://docs.aws.amazon.com/cloud9/latest/user-guide/sample-php.html)
<?php
  
  print("\nThe sum of 2 and 3 is 5.");


  $sum = (int)$argv[1] + (int)$argv[2];


  print("\nThe sum of $argv[1] and $argv[2] is $sum.");
?>

[B]getting error

[/B]Running PHP script home/ubuntu/environment/cloud_ide1/dev/hello.php  (source location)           
(standard_in) 1: syntax error           
bash: line 9: [: -eq: unary operator expected                                   
Could not open input file: home/ubuntu/environment/cloud_ide1/dev/hello.php

---

### Post by Holger_Gehrke on 2019-07-14
Whatever is still wrong, it's not the PHP-Code. I copied your code into an editor, saved it as 'test.php' and ran it from the shell with 'php test.php 1 1' and got the expected results. 
From the errors you get I believe the IDE calls some shell-script to run your program and passes a lot of options to that script. Some wrong setting in the IDE is breaking the script.

Holger

---

### Post by aruneshdutta on 2019-07-15
I restarted and passed arguments as shown [here]("https://docs.aws.amazon.com/cloud9/latest/user-guide/sample-php.html") with filename.php 10 12, it shows perfect output but don;t know why it's shows syntax error above the output and -eq unary operator expected

```

___
<?php
  print("Hello, World!");


  print("\nThe sum of 2 and 3 is 5.");


  $sum = (int)$argv[1] + (int)$argv[2];


  print("\nThe sum of $argv[1] and $argv[2] is $sum.");
?>

```

output
_____
Running PHP script /home/ubuntu/environment/cloud_ide1/dev/hello.php            
(standard_in) 1: syntax error           
bash: line 9: [: -eq: unary operator expected                                   
Hello, World!       
The sum of 2 and 3 is 5.                
The sum of 10 and 12 is 12.

---

### Post by wildmanne39 on 2019-07-15
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

