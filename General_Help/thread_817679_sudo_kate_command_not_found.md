---
title: "sudo: kate: command not found"
date: 2008-06-03
forum: General Help
---

### Post by jason1500 on 2008-06-03
I am very new to linux and I really want to like it but the simplest things like editing a text file is PITA!

Alright I'm using the newest version of kubuntu with KDE.  I want to edit /etc/modules so I can load a new module(ndiswrapper) on startup.  I tried editing it by opening it with kate but it wouldn't save.  

So I open Konsole and typed
kdesu kate /etc/modules
and I type in my password this is what I get back
sudo: kate: command not found

:(

---

### Post by wolfen69 on 2008-06-03
try
```
sudo nano /etc/modules
```
to save, do ctrl-x, then Y, then enter.

---

### Post by aysiu on 2008-06-03
Are you using KDE 4 by chance? If so, this might help: ```
/usr/lib/kde4/bin/kdesudo /usr/lib/kde4/bin/kate /etc/modules
```

---

### Post by Coplen on 2008-06-04
aptitude install kate

or try aptitude install kate4

I'm not sure which it might be under.

I'm assuming the program isn't there.

---

### Post by jason1500 on 2008-06-04
> **aysiu said:**
> Are you using KDE 4 by chance? If so, this might help: ```
/usr/lib/kde4/bin/kdesudo /usr/lib/kde4/bin/kate /etc/modules
```

yes I am. but I don't know what I'm suppose to do with that code you posted:confused:  thanks

but the nano thing Wolfen69 posted did the trick.

---

### Post by angry_johnnie on 2008-06-04
It must be using a different command to launch kate.  Maybe something like kate-kde4.

you could:

```
ls -a /usr/bin | grep kate
```

and see what it's called (given it actually is inside /usr/bin/).

Or you could try the **edit menu** utility, just to see what the command is.

Edit:  I was thinking it might be easier to just type **ka** and then press the tab key twice.  It should give you a list of all possible commands that start with ka.  kate, whatever it's being called, should be there.

---

### Post by Jonathan Harford on 2008-06-19
I'm having the same issue (Kubuntu-KDE4 8.04). Is there a way to make "kdesu kate" actually work?

How do most people edit config files?

---

### Post by sisco311 on 2008-06-19
[http://ubuntucat.wordpress.com/2008/06/09/how-to-use-konqueror-or-kate-as-sudo-in-kubuntu-kde-4-remix/](http://ubuntucat.wordpress.com/2008/06/09/how-to-use-konqueror-or-kate-as-sudo-in-kubuntu-kde-4-remix/)

---

### Post by Jonathan Harford on 2008-06-19
You're a star.

---

### Post by aysiu on 2008-06-19
Even though someone commented in my blog about exporting the path, I haven't found a way to do it so that *kdesu kate* actually works. If someone can give me the exact command that will make /usr/lib/kde4/bin part of the *kdesu* path, please let me know.

---

### Post by sisco311 on 2008-06-19
> **aysiu said:**
> Even though someone commented in my blog about exporting the path, I haven't found a way to do it so that *kdesu kate* actually works. If someone can give me the exact command that will make /usr/lib/kde4/bin part of the *kdesu* path, please let me know.

sudo is compiled with the *--with-secure-path* option. You can't change the path for sudo in a config file.

You can force sudo to use the $PATH variable:
```
sudo  env PATH=$PATH [I]command
[/I]kdesu  env PATH=$PATH *command*
```quick workaround:
1.) append the $PATH variable with the */usr/lib/kde4/bin *directory[I]:
[/I]> export PATH=$PATH:/usr/lib/kde4/bin2.) create aliases:
> alias sudo="sudo env PATH=$PATH"
alias kdesu="kdesu env PATH=$PATH"
alias kdesudo="kdesudo env PATH=$PATH"[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/192651](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/192651)
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/50797](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/50797)

---

### Post by aysiu on 2008-06-19
> **sisco311 said:**
> sudo is compiled with the *--with-secure-path* option. You can't change the path for sudo in a config file.

You can force sudo to use the $PATH variable:
```
sudo  env PATH=$PATH [I]command
[/I]kdesu  env PATH=$PATH *command*
```quick workaround:
1.) append the $PATH variable with the */usr/lib/kde4/bin *directory[I]:
[/I]2.) create aliases:
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/192651](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/192651)
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/50797](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/50797)
That seems quite a lot of trouble to go through. Does it stick? Or will that have to be redone after every log out?

---

### Post by sisco311 on 2008-06-19
> **aysiu said:**
> That seems quite a lot of trouble to go through. Does it stick? Or will that have to be redone after every log out?

To make the changes permanent add this lines:
> 
export SUDOPATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/usr/lib/kde4/bin 			 		

alias sudo="sudo env PATH=$SUDOPATH"
alias kdesu="kdesu env PATH=$SUDOPATH"
alias kdesudo="kdesudo env PATH=$SUDOPATH" 			 		
to the */etc/bash.bashrc* file.

The SUDOPATH variable is the default sudo path variable + /usr/lib/kde4/bin directory.

---

### Post by virtudtierra on 2008-08-12
to access as root to kate-kde4 o k3b, etc., I remove the package called kdesudo  and just reinstall the package called kdesu-kde4.

$ sudo su
$ apt-get update
$ apt-get upgrade
$ apt-get remove --purge kdesudo
$ apt-get install --reinstall kdesu-kde4
$ exit


Now, I can run KDE3.X or KDE4 applications with no problem


more information at the following link
[http://www.chilewarez.org/index.php?showtopic=610061](http://www.chilewarez.org/index.php?showtopic=610061)

---

### Post by adambh on 2009-04-14
> **jason1500 said:**
> I am very new to linux and I really want to like it but the simplest things like editing a text file is PITA!

Alright I'm using the newest version of kubuntu with KDE.  I want to edit /etc/modules so I can load a new module(ndiswrapper) on startup.  I tried editing it by opening it with kate but it wouldn't save.  

So I open Konsole and typed
kdesu kate /etc/modules
and I type in my password this is what I get back
sudo: kate: command not found

:(

kate is a KDE command, if you're using Gnome, try "gksudo gedit" in it's place

---

