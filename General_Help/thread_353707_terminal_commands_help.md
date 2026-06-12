---
title: "terminal commands help"
date: 2007-02-05
forum: General Help
---

### Post by burmanabhay88 on 2007-02-05
i'm new to ubuntu and linux as such. can some one please tell me how to change directories in terminal.
i was using WinXp earlier, where in command prompt we used commands such as cd(to change directory), cd..(to come out of directory), copy,xcopy,del,md,etc....
Could somebody please tell me equivalent commands.
Thanks

---

### Post by ~LoKe on 2007-02-05
cd is the same.

```
cd /home
```
```
cd ~/Desktop
```
```
cd /var/
```
> loke@x04d:~$ cd ~/Movies/The.Prestige
[email]loke@x04d:~/Movies/The.Pres[/email]tige$ cd ..
loke@x04d:~/Movies$ cd ..
loke@x04d:~$ cd Movies
loke@x04d:~/Movies$ 

---

### Post by burmanabhay88 on 2007-02-05
could u please give some more commands
could u with an example tell me how exactly to move from one directory to another, and feew more commands. make it as simple as possible, i'm very new to linux OS

---

### Post by UbLnoy on 2007-02-05
Hello burmanabhay88,

You can try these:

cd ..  will take you up one directory
ls      will "list" the contents of a directory
pwd   will print the working directory

---

### Post by ZipoTe on 2007-02-05
here you are:

change directory:

```
cd ..
```

(yes, with a space between "cd" and "..")

make a new directory:

```
mkdir [name of the new directory]
```

make a new file:

```
touch [name of the file]
```

list of all you have in one directory:

```
ls
```

(you can use dir like windows, but i prefer ls)



imagine you are having problems with some program, don't worry only type:

```
ps -ax
```

you will see a list of programs running, look at the numberof your program (PID) and type:

```
kill -9 [PID of the program is giving you problem]
```


and of course, the most important:

```
sudo apt-get install [name of the programe]
```
```
sudo apt-get update
``` to update your sources list ^^
> sudo apt-get upgrade

and many many many others...

---

### Post by PetePete on 2007-02-05
why dont u just look this up on google.... theres millions of pages with various linux commands.

2 seconds effort and i foudn this
[http://www.reallylinux.com/docs/admin.shtml](http://www.reallylinux.com/docs/admin.shtml)

---

### Post by UbLnoy on 2007-02-05
Found this too:

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by ZipoTe on 2007-02-05
Of course google is your friend :P and these forums also, so before asking something, chech it out ^^ doing this you will learn a lot, believe me. for the next time you know ;)

Bye!!

---

### Post by reclusivemonkey on 2007-02-05
> **burmanabhay88 said:**
> could u please give some more commands
could u with an example tell me how exactly to move from one directory to another, and feew more commands. make it as simple as possible, i'm very new to linux OS

For the manual for any command, use

```

man *command*

```

You can also search for keywords within all the manuals with

```

man -k *keyword*

```

or 

```

apropos [i]keyword[/]

```

If you want to learn the CLI, I highly recommend RUTE;

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

---

