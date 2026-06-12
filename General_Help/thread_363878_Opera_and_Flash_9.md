---
title: "Opera and Flash 9"
date: 2007-02-17
forum: General Help
---

### Post by jimbob on 2007-02-17
I tried to install Flash 9 in Opera and the installation failed by telling me that Opera is not supported.

Why would anyone choose Opera as a browser if it can't play flash videos or am I missing something?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Colonel Kilkenny on 2007-02-17
> **jimbob said:**
> I tried to install Flash 9 in Opera and the installation failed by telling me that Opera is not supported.

Why would anyone choose Opera as a browser if it can't play flash videos or am I missing something?

Opera can play flash, Adobe choosed to release flash 9 for linux without support for Opera (and said that support will be coming later). It has nothing to do with Opera.
Anyway, just install it to Firefox and then copy the file from /usr/lib/firefox/plugins to /usr/lib/opera/plugins and you have working (with little problems) flash 9 in Opera as well.

---

### Post by Maestro23 on 2007-02-17
Running Edgy 6.10 with the flash plugin from the repositories.  Just d/l and installed .deb opera pkg from their site.  Flash sites are working just fine in opera like they do in firefox for me.

---

### Post by r4ik on 2007-02-17
You can add the following to your /etc/apt/sources.lst

Code:

## Seveas&#8217; packages ## (GPG key: 1135D466) deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas all

and the in terminal type
Code:

sudo aptitude install flashplugin-nonfree



Credits croppyboy.

---

### Post by burritomasters on 2007-08-11
> **Colonel Kilkenny said:**
> 
Anyway, just install it to Firefox and then copy the file from /usr/lib/firefox/plugins to /usr/lib/opera/plugins and you have working (with little problems) flash 9 in Opera as well.

which file?

---

### Post by Hayabusarider on 2007-08-23
ya anyone know the files that need moved?

---

### Post by gundumfx on 2007-08-23
> **Maestro23 said:**
> Running Edgy 6.10 with the flash plugin from the repositories.  Just d/l and installed .deb opera pkg from their site.  Flash sites are working just fine in opera like they do in firefox for me.

can i get a link about what you are talking about downloading the deb packages
thanks

---

### Post by evets on 2007-10-23
> **burritomasters said:**
> which file?

I'm thinking libflashplayer.so. Except I don't know how to do that 'cause I keep getting a no permission error. Sadly, I haven't learnt to properly use of the command line yet.

---

### Post by Maestro23 on 2007-10-23
> **evets said:**
> I'm thinking libflashplayer.so. Except I don't know how to do that 'cause I keep getting a no permission error. Sadly, I haven't learnt to properly use of the command line yet.

> sudo cp libflashplayer.so....

You are dealing with directories owned by **roo**t.  You need** root** permission to do anything in there. Hence the** sudo** command.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by evets on 2007-10-23
> **Maestro23 said:**
> You are dealing with directories owned by **roo**t.  You need** root** permission to do anything in there. Hence the** sudo** command.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


Yes, I got that. But, what is the syntax to copy it from firefox to opera. Here's what I (feebily) attempted...

sudo cp -r /usr/lib/firefox/plugins/libflashplayer.so  usr/lib/opera/plugins

sudo cp -r /usr/lib/firefox/plugins/libflashplayer.so  usr/lib/opera/plugins/libflashplayer.so

Thanks

---

### Post by Warpnow on 2007-10-23
Any idea why they wouldn't support opera in linux? 

I <3 opera in linux. :(

---

### Post by evets on 2007-10-23
> **Warpnow said:**
> Any idea why they wouldn't support opera in linux? 

I <3 opera in linux. :(

I've been wondering that, myself. You would think it's about choice, and that being the case, they would offer as many stable choices of popular products as possible.

---

