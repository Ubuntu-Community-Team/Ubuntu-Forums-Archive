---
title: "Cannot find installation? Wine?"
date: 2007-04-03
forum: General Help
---

### Post by CubicVirtuoso on 2007-04-03
OK, here is my situation. I would post this in the how-to wine forum but I don't think its relavent there anymore. I am trying to get wine to work on 64bit Feisty however I accidentally replaced all the library files in the lib32 folder :( yea yea I'm stupid.

Anyway I got that all fixed and went ahead and dpkg'ed wine... Maybe the following code will make things clear:

```
cvirtuoso@cvirtuoso-desktop:~/Desktop$ sudo dpkg --force-architecture -i wine_0.9.34~winehq0~ubuntu~6.06-1_i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package wine.
(Reading database ... 118281 files and directories currently installed.)
Unpacking wine (from wine_0.9.34~winehq0~ubuntu~6.06-1_i386.deb) ...
Setting up wine (0.9.34~winehq0~ubuntu~6.06-1) ...

cvirtuoso@cvirtuoso-desktop:~/Desktop$ wine
bash: /usr/bin/wine: No such file or directory
cvirtuoso@cvirtuoso-desktop:~/Desktop$ cd /usr/local
cvirtuoso@cvirtuoso-desktop:/usr/local$ ls
bin  etc  games  include  lib  man  sbin  share  src
cvirtuoso@cvirtuoso-desktop:/usr/local$ which wine
/usr/bin/wine
cvirtuoso@cvirtuoso-desktop:/usr/local$ cd /usr/bin
cvirtuoso@cvirtuoso-desktop:/usr/bin$ ls -l wine
-rwxr-xr-x 1 root root 4656 2007-04-01 19:37 wine
cvirtuoso@cvirtuoso-desktop:/usr/bin$ 

```

Essentially when I do a command like wine or winecfg it doesn't exist. I can see the executable in /usr/bin and which is returning that directory. I tried uninstalling by doing a dpkg -r wine, then reinstalling but it all does the same thing. 

Can someone tell me what is going wrong?! Thanks so much!

---

### Post by jbumgar on 2007-04-03
I had to install wine from Synaptic Package Manger.  The first time I did it from add/remove and it didn't work.

---

### Post by CubicVirtuoso on 2007-04-04
> **jbumgar said:**
> I had to install wine from Synaptic Package Manger.  The first time I did it from add/remove and it didn't work.

I can't do it that way because this is on 64bit. Synaptic won't pick up wine because its only for 32 bit distros.

---

