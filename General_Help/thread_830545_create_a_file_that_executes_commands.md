---
title: "create a file that executes commands?"
date: 2008-06-15
forum: General Help
---

### Post by pwnage101 on 2008-06-15
i've been searching it forever but came up with nothing. i know it's probably just a matter of searching the right thing but i dont know what it is.

i just want to know how to make a file that will run a simple command when i click on it.

thanks

---

### Post by drs305 on 2008-06-15
This is normally done with small files called scripts, normally associated with BASH. If you do a search for those two words you will probably be able to find something useful. 

Here are some links:
[http://floppix.ccai.com/scripts1.html]("http://floppix.ccai.com/scripts1.html")
[http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html]("http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html")
[http://www.linuxconfig.org/Bash_scripting_Tutorial]("http://www.linuxconfig.org/Bash_scripting_Tutorial")

The basic steps:
Create a BASH script and save it.
Make it executable  ( chmod a+x scriptname ) .
Run it.

---

### Post by lut4rp on 2008-06-15
Here's a website, from where I learned when I was a n00b :D
[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)

---

### Post by vishzilla on 2008-06-15
> **pwnage101 said:**
> i've been searching it forever but came up with nothing. i know it's probably just a matter of searching the right thing but i dont know what it is.

i just want to know how to make a file that will run a simple command when i click on it.

thanks

If it is a single command, you can create a launcher. Else you can use bash scripts for multiple commands

---

### Post by pwnage101 on 2008-06-16
thanks alot everybody!

created my first bash script called javabash (just a temporary name)

here are the contents of the script:
```
#!/bin/bash
javac $1".java"
java $1
rm $1".class"
```

and here's what it does:

test.java
```
public class test
{
   public static void main(String[] args)
   {
      System.out.println(6 * 7);
   }
}
```

in terminal:
```
troy@troy-desktop:~$ cd /home/troy/Desktop
troy@troy-desktop:~/Desktop$ javabash test
42
troy@troy-desktop:~/Desktop$
```

i'm somewhat jittery right now:)

---

