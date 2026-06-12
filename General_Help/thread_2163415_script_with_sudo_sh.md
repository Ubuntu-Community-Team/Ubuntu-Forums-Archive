---
title: "script with sudo sh"
date: 2013-07-18
forum: General Help
---

### Post by marilia15 on 2013-07-18
Hi,

I'm a beginner in linux so excuse me if my question is too easy.

I want to make a script to install a program (ROS) and I need to write this line:
```


 sudo sh -c 'echo "TEXT VARIABLE TEXT" > systemFile'  # to write in systemaFile I need sudo sh


``` 
If echo is just fixed text, it works. 
If echo is text + variable it doesn't work. The variable is the codename of my linux version  (in 12.10 is "quantal").

I've tried with:

 

 ```
read f1 < <(lsb_release -a | grep Code* | cut  -f2)   #codename is writted in variable $f1
echo $f1 # retruns "quantal" as I expected
sudo sh -c 'echo "TEXT $f1 TEXT" > systemFile'  #f1 is empty, WHY?


```


Then I have to assign the variable inside the same instruction sudo sh, for example: ```

sudo sh -c ' read f1 < <(lsb_release -a | grep Code* | cut  -f2) ; echo "TEXT $f1 TEXT" > systemFile' 

 sh: 1: Syntax error: redirection unexpected

```


The error is in the first instruction of sudo sh  (read f1  < <(lsb_release -a | grep Code* | cut  -f2)),  executed without sudo sh it works, but inside sudo sh -c it doesn't work. 

Anyone knows why? How can I do this?
Thanks in advance

---

### Post by Impavidus on 2013-07-18
The shell you start with **sh -c** doesn't inherit the variables you set in your first shell:```
$ f=hello
$ echo $f
hello
$ bash
$ echo $f
#Variable not defined
$ exit
exit
$ echo $f
hello

```
This can be fixed using **export** (or **setenv**, depending on your shell), turning it into an environment variable:```
$ export f=hello
$ echo $f
hello
$ bash
$ echo $f
hello #Variable defined
$ sudo echo $f
[sudo] password for user: 
hello
$ exit
exit
```
Also, it may be easier not to use **sudo** in a script, but call the entire script with **sudo**.

---

### Post by steeldriver on 2013-07-18
Simple answer - single quotes prevent shell expansion i.e. everything within single quotes gets interpreted as a literal string

You could backslash-escape the inner quotes e.g.

```
$ f1="something" 
$ sh -c 'echo "TEXT $f1 TEXT"'
TEXT  TEXT
$
$ sh -c "echo \"TEXT $f1 TEXT\""
TEXT something TEXT
$ 

```

or for your particular case (echoing a line to a system file) a better solution might be

```
echo "TEXT VARIABLE TEXT" | sudo tee systemFile
```

but probably the best way around this is to execute the whole install script with sudo rather than having multiple individual 'sudo sh -c ...' subshells

---

### Post by Vaphell on 2013-07-18
you don't have to grep anything to get the codename, lsb_release supports -c (codename) and -s (short version)

```
$ lsb_release -h
Usage: lsb_release [options]

Options:
  -h, --help         show this help message and exit
  -v, --version      show LSB modules this system supports
  -i, --id           show distributor ID
  -d, --description  show description of this distribution
  -r, --release      show release number of this distribution
 ** -c, --codename     show code name of this distribution**
  -a, --all          show all of the above information
 ** -s, --short        show requested information in short format**
```

```
$ lsb_release -sc
lucid
$ sh -c "echo 123 $(lsb_release -sc) 456"
123 lucid 456

```

---

### Post by zero2xiii on 2013-07-18
+1 for Vaphell,

Thats how I would have done it... Assuming your example is the exact script you are running.

Also +1 for steeldriver,

In a second case I would rather go with his/her recommendation:

> echo "TEXT VARIABLE TEXT" | sudo tee systemFile

Cheers

---

