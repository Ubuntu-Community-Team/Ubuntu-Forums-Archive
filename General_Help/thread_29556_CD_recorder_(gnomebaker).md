---
title: "CD recorder (gnomebaker)"
date: 2005-04-24
forum: General Help
---

### Post by ubuntu27 on 2005-04-24
Hey guys! Thanks for helping me out for the previuos problems that I had  ;-) 

I downloaded gnomebaker_0.3-3_i386.deb from a link that [http://gnomebaker.sourceforge.net/](http://gnomebaker.sourceforge.net/) displays.

and, I tried to install.. 

Here is what I got:

ubuntu27@ubuntu27:~$ sudo dpkg -i gnomebaker_0.3-3_i386.deb
(Reading database ... 65083 files and directories currently installed.)
Preparing to replace gnomebaker 0.3-3 (using gnomebaker_0.3-3_i386.deb) ...
Unpacking replacement gnomebaker ...
dpkg: dependency problems prevent configuration of gnomebaker:
 gnomebaker depends on cdda2wav; however:
  Package cdda2wav is not installed.
 gnomebaker depends on mpg321; however:
  Package mpg321 is not installed.
 gnomebaker depends on sox; however:
  Package sox is not installed.
dpkg: error processing gnomebaker (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnomebaker
ubuntu27@ubuntu27:~$


Can sombody help me?

---

### Post by hobnob on 2005-04-24
Gnomebaker is in the Universe repository, so all you need to do is install it using apt-get like so:```
$ sudo apt-get install gnomebaker
```Apt-get will take care of the dependancy problems you're experiencing.

Hope this helps!

---

### Post by ubuntu27 on 2005-04-24
:( Look at this:

ubuntu27@ubuntu27:~$ sudo apt-get install gnomebaker
Password:
Reading package lists... Done
Building dependency tree... Done
gnomebaker is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnomebaker: Depends: cdda2wav but it is not going to be installed
              Depends: mpg321 but it is not going to be installed
              Depends: sox but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ubuntu27@ubuntu27:~$

---

### Post by Nano on 2005-04-24
[QUOTE=ubuntu27]:( Look at this:

ubuntu27@ubuntu27:~$ sudo apt-get install gnomebaker
Password:
Reading package lists... Done
Building dependency tree... Done
gnomebaker is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnomebaker: Depends: cdda2wav but it is not going to be installed
              Depends: mpg321 but it is not going to be installed
              Depends: sox but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ubuntu27@ubuntu27:~$[/QUOTE]
 You can always install them by hand.

sudo apt-get install cdda2wav
sudo apt-get install mpg321
sudo apt-get install sox

---

### Post by hobnob on 2005-04-24
Or alternatively, force apt to install the missing packages by```
$ sudo apt-get -f install
```

---

### Post by ubuntu27 on 2005-04-24
Alright!! Thaanks guys!!! Now it works. hehe,.

---

### Post by MetalMusicAddict on 2005-04-24
Cool man. You should give this guide a look. Its invaluable.

[Unofficial Ubuntu 5.04 Starter Guide](http://ubuntuguide.org/)

Tons of need-to-know stuff. Enjoy the ride man. It gets easier. ;)

I really like Gnomebaker. I think it stacks up well to K3B.

---

### Post by Nano on 2005-04-24
Reading gnomebaker's site I found out they're planning to support burn on the fly but can already do it...
Weird...

---

