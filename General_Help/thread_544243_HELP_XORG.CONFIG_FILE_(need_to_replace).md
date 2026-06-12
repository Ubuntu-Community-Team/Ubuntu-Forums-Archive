---
title: "HELP: XORG.CONFIG FILE (need to replace)"
date: 2007-09-06
forum: General Help
---

### Post by lemonwonder on 2007-09-06
Hi.

I have ubuntu PPC installed on my PS3.

I edited the xorg.conf/config or whateva its called and now cant get it to go to graphical desktop etc.

I can login thru terminal/kboot or whateva it is, and I need a command that will download and replace the xorg.conf/config file.

THAX!

---

### Post by southernman on 2007-09-06
To replace/rebuild your xorg.conf file... or whateva! :p You'll have to reconfigure the xserver:

```
sudo dpkg-reconfigure xserver-xorg
```

is the command you need to run.

FWIW, next time you need to edit a system file do yourself a favor and do this first:

```
sudo cp /path/to/name/of/file /path/to/name/of/file.backup
```

this way when you screw the pooch, you can just reverse the command above and reboot.

Good Luck & HTH's

---

### Post by lemonwonder on 2007-09-07
Thx for ur help but it relly didnt help. I dnt know how to reconfigure it, so i just went thru all the options clicking ok, then it loaded and sed:

Cannot load x server (your graphical manager) blah blah blah lblah

I want to DOWNLOAD the alredy ok file... is there a way to download it?

---

### Post by superfunkymonkey on 2007-12-17
I'm a bit late here, but I hope this is useful to someone.

sudo dpkg-reconfigure -phigh xserver-xorg

The -phigh option will automatically answer all the questions for you.

Matt

---

