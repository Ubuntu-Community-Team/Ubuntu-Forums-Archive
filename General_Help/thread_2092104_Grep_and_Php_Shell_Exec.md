---
title: "Grep and Php Shell_Exec"
date: 2012-12-06
forum: General Help
---

### Post by spec36 on 2012-12-06
Hey Everyone,

I'm having a really hard time figuring this one out. 

I am running Ubuntu and trying to write a PHP script that will run a grep command that contains a php variable as part of the grep.

Example of my code that works:
[PHP]$cmd = shell_exec('cat data.txt | grep -i /11 -B 1 -A 25');[/PHP]There is other php code that writes the grep results to a file that I have not included since the problem resides in the command above.

I want to include a variable called year in my grep command instead of the "/11", something like this:
[PHP]$cmd = shell_exec('cat data.txt | grep -i $YEAR -B 1 -A 25');[/PHP]I have tried multiple concatenation attempts to make this work, but all to no avail.

error log shows:
[PHP]Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
cat: write error: Broken pipe[/PHP]So I know all the concatenation attempts I have made are sending the grep command incorrectly to the shell.

I have spent hours on this and am starting to pull my hair out. Anyone have any ideas?

I think I have to do something like this to the variable, but unsure how to set it up within the original php code posted.
[PHP]${year}[/PHP]Your help is greatly appreciated.

Thank You.

---

### Post by SeijiSensei on 2012-12-06
```
$cmd = shell_exec('cat data.txt | grep -i $YEAR -B 1 -A 25');  
```

Encase the command in double quotes like this:

```
$cmd = shell_exec("cat data.txt | grep -i $YEAR -B 1 -A 25");  
```

As in the shell, strings in single quotes are treated literally, while those in double quotes are evaluated after the variables are replaced with their values.

You know that PHP has built-in functions to handle regular expressions, right?  However [POSIX]("http://php.net/manual/en/book.regex.php") regular expressions have been deprecated in favor of [Perl-compatible]("http://php.net/manual/en/book.pcre.php") ones.

---

### Post by spec36 on 2012-12-06
Thanks for the response SeijiSensei. I'm kicking myself, because I had it in double quotes for the longest time. I knew that was right.

Turns out the code is in a function. The $year variable is outside the function. I forgot to give the function the $year variable as input.

Dang it.

Thanks Again
--spec36

---

