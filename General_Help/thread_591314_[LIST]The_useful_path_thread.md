---
title: "[LIST]The useful path thread"
date: 2007-10-25
forum: General Help
---

### Post by holihue on 2007-10-25
In this thread i will post useful paths.



[SIZE="5"]**Your home location**[/SIZE]
/home/your_user_name


[SIZE="5"]**Where to simply edit commands**[/SIZE]
.bashrc
/home/your_user_name/.bashrc

Example:
if you want to install, and want to run install [package] instead of sudo apt-get install [pacage]
```
alias install='sudo apt-get install'
```
[COLOR="Blue"]Link:[/COLOR]
[http://www.faqs.org/docs/abs/HTML/files.html]("http://www.faqs.org/docs/abs/HTML/files.html")


[SIZE="5"]**Configuration file for xorg**[/SIZE]
xorg.conf:
/etc/X11/xorg.conf


[SIZE="5"]**The local boot scrip**t[/SIZE]
rc.local:
/etc/rc.local


[SIZE="5"]**Where apt-get, synaptics, aptitude, etc. saves the downloaded .deb file**[/SIZE]
/var/cache/apt/archives/


[SIZE="5"]**Boot order lis**t[/SIZE]
menu.lst
/boot/grub/menu.lst


[SIZE="5"]**The file where to get repositories from**[/SIZE]
sources.list
/etc/apt/sources.list


[SIZE="5"]Handle what is mounted and where[/SIZE]
fstab
/etc/fstab




If you know about a path to a file or files, I would love if you post it.
And then add it to the list.

---

### Post by holihue on 2007-10-25
Anyone knows about other paths?(bump)

---

### Post by anaconda on 2007-10-25
/etc/fstab
Handles what is mounted and where.

---

### Post by Hamnvik on 2007-10-27
**[SIZE="2"]/home/your username[/SIZE] !!**

it's the most important of them all.

---

### Post by thelocust on 2007-10-27
/home/username/.bashrc
 
to add alias's for terminal like ```
alias rm='rm -i'
``` so that you don't delete the wrong things. 
 
[URL="http://tldp.org/LDP/abs/html/sample-bashrc.html"]example .bashrc file
[/URL]

---

### Post by holihue on 2007-10-29
Thanks, The list is update now.:)

I will look for more useful locations, and files.

---

