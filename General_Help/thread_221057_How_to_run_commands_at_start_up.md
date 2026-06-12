---
title: "How to run commands at start up"
date: 2006-07-22
forum: General Help
---

### Post by andyp11 on 2006-07-22
I've a few modprobe commands that I'd like run at start up rather than having to do them manually. Anyone help?

I suppose at system start up rather that desktop log in, 'tho, in reality, no practical difference.

---

### Post by Ziox on 2006-07-22
if you are running gnome then, system => preferences => sessions => Startup Programs tab, and click Add, then just enter the command that you use.

---

### Post by 5-HT on 2006-07-22
To load specific modules on boot, you can append their names in */etc/modules *(one line per module)[I].

[/I]HTH

---

### Post by andyp11 on 2006-07-23
Yep the /etc/modules file is the place. Thanks

---

### Post by MiKom on 2007-05-26
But how can I run some commands as a root? In SUSE I just need to add the commands to /etc/init.d/boot.local or to /etc/conf.d/local.start in Gentoo. Is there any similar file in Ubuntu? To be exact, I want to run commands that will unlock the sound in Quake 3 engine games when using teamspeak.
These commands are:

echo 'quake3.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'quake3.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss

They need to be run as a root.

---

### Post by Bachstelze on 2007-05-26
Add your commands to /etc/rc.local

---

