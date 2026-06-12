---
title: "Apt-get problems"
date: 2005-10-05
forum: General Help
---

### Post by bogoliubov on 2005-10-05
Hello there. I just tried to update ubuntu by doing
"sudo apt-get update". But I got a lot of errors, mainly of the type "404 not found". 

Does anyone know how I fix this? I attached a textfile of the output...

Ohh, by the way; does anyone know how to use the multimedia keys to switch tracks in Xmms? I get the gnome volume working, but Xmms will not. In Fedora, which I used before, I used some "Acme" rpm, but I can't find it for ubuntu...

---

### Post by sd_ap on 2005-10-05
[QUOTE=bogoliubov]Hello there. I just tried to update ubuntu by doing
"sudo apt-get update". But I got a lot of errors, mainly of the type "404 not found". 
Does anyone know how I fix this? I attached a textfile of the output...
Ohh, by the way; does anyone know how to use the multimedia keys to switch tracks in Xmms? I get the gnome volume working, but Xmms will not. In Fedora, which I used before, I used some "Acme" rpm, but I can't find it for ubuntu...[/QUOTE]


I got the same thing...what caused it for me was having the backports in my sources.list in /etc/apt.  Once that was removed, the 404s went away.  The packages not found though...I cant find a fix for that as I am suffering from the same thing!

---

### Post by ubuntumaneh on 2005-10-05
[QUOTE=bogoliubov]Hello there. I just tried to update ubuntu by doing
"sudo apt-get update". But I got a lot of errors, mainly of the type "404 not found". 
Does anyone know how I fix this? I attached a textfile of the output...[/QUOTE]

   Backports in Mirrormax is off, I think. For the time being you can try to modify your /etc/apt/source.list Here is a piece of mine, which is working:

----------------------------------------------------------
## 
## Multiverse and other repositories (use with caution)
## 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

#backports

#### the official one

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

#### non-official ones (for help: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) )

#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-backports main universe multiverse restricted
deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-extras main universe multiverse restricted

#deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports-staging main universe multiverse restricted

---------------------------------------------------

  cheers

---

### Post by Sarhath on 2005-10-06
Hi,
I'm having the same problem, but the other links didn't help. I still can't get anything other than what the defaults are. Any ideas? I'm a newbie, so the problem might be something obvious...
thanks. ^^

---

