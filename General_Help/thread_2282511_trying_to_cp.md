---
title: "trying to cp"
date: 2015-06-14
forum: General Help
---

### Post by Miykel on 2015-06-14
G'day; Been trying to learn how to cp , wrote a small text file and saved it to Downloads, trying to cp it to Documents, practice, but I get :

miykel@miykel:~$ cp Downloads/Trial/ /Home/miykel/Documents/
cp: cannot stat ‘Downloads/Trial/’: Not a directory
miykel@miykel:~$ 

What am I doing wrong please..
Regards Miykel

---

### Post by entropy1 on 2015-06-14
I think there are two mistakes.  First, remove the slash after Trial.  Second, the "H" in "Home" should be lower case.  The correct command should be
```
cp Downloads/Trial /home/miykel/Documents/
```

---

### Post by Miykel on 2015-06-14
entropy1...Thank you so much, reading about which command does what and actually doing it is somewhat different...thanks again
Regards Miykel

---

### Post by Bashing-om on 2015-06-14
Miykel; Hello ;

Syntax, grasshopper.
in the expression " cp Downloads/Trial[color=red]/[/color] that trailing '/' on /Trail indicates to the system that this is a directory rather than a file .

So let's look at what you have ,, with your present working directory (PWD) at the default location of /home; what returns:
```

ls -al Downloads

```
in that output do you see the file " Trail " ?

Now to copy (cp) the target file to the desired destination; one could do a number like:
```

cp Downloads/Trial /home/miykel/Documents/

```
There is a shortcut for "/home/miykel" ( ~/ ) try :
```

ls -al ~/

```
Though not required the trailing '/' in Documents/  explicitly declares the destination as a directory, and is good practice.

2nd, linux is case sensitive; Home does not equal home. Your home is denoted with the lower case 'h' .

Hope this helps .

[INDENT][INDENT]all a process of learning
[/INDENT][/INDENT]

---

### Post by sammiev on 2015-06-14
Hi,

[This]("http://www.thegeekstuff.com/2013/03/cp-command-examples/") can be used for reference. It has helped me in the past.

---

