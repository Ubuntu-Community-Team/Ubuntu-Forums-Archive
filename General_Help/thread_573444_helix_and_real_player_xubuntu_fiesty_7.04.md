---
title: "helix and real player xubuntu fiesty 7.04"
date: 2007-10-11
forum: General Help
---

### Post by larryfroot on 2007-10-11
Hello people. 

I have downloaded the realplayer 10 for Linux  from the realplayer site...tried to install it to /usr/local/realplayer after a mkdir for the realplayer folder then after the mkdir which had to be done in sudo mode I cd'd into the folder the binary was in (which happened to be in my home directory) and ran it. All went well...the installer asked me where I wanted it to go and I told it /usr/local/realplayer (after reading some advice about where it should install on this forum) but it stalled with a permission denied as I suddenly did not have sudo credentials anymore. 

SO I am stumped on two counts. Firstly is the folder that helix looks for realplayer really /usr/local/realplayer? Secondly do I have to mkdir a folder called realplayer, or does the installer do that all by itself...and secondly, how the bleeeeep do I get to attain and stay in sudo for the duration of the install. Or do I really have to run as root? And IF I do run as root - would rather not...how do I do that?

Thank you for any help you guys and powerful, fiesty women with attitude can give me..(dream on froot old son, dream on...)

---

### Post by por100pre1 on 2007-10-11
You are using Feisty, good. Do this:

```
sudo su -c 'echo deb http://archive.canonical.com/ubuntu feisty-commercial main >> /etc/apt/sources.list'
```

```
sudo aptitude update && sudo aptitude install realplay
```

This will install a .deb from the Canonical commercial repository.

---

### Post by larryfroot on 2007-10-12
Thanks for the help...but surprisingly it hasn't done the trick...I now get a message saying

The following components are required  audio/mp3

Tried apt-get with 'audio/mp3' but unsurprisingly it failed! 

I'm still ???? Any help appreciated, thanks!

---

