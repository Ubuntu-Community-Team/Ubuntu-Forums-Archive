---
title: "Update of audio pacakges causes no sound"
date: 2018-04-24
forum: General Help
---

### Post by Mark_in_Hollywood on 2018-04-24
After apt-get update, apt-get upgrade, about 8 sound related packages were installed.

Rhythmbox produced no sound. From Sound (Setting) Test Sound (Left Right) produces no sound.

Running 

```
mark@Lexington:~$ grep " install " /var/log/dpkg.log
2018-04-03 07:53:52 install linux-image-4.13.0-38-generic:amd64 <none> 4.13.0-38.43~16.04.1
2018-04-03 07:53:54 install linux-image-extra-4.13.0-38-generic:amd64 <none> 4.13.0-38.43~16.04.1
2018-04-03 07:53:57 install linux-headers-4.13.0-38:all <none> 4.13.0-38.43~16.04.1
2018-04-03 07:54:01 install linux-headers-4.13.0-38-generic:amd64 <none> 4.13.0-38.43~16.04.1
2018-04-03 14:14:30 install libglade2-0:amd64 <none> 1:2.6.4-2
2018-04-03 14:14:30 install python-glade2:amd64 <none> 2.24.0-4ubuntu1
2018-04-03 14:14:30 install python-nut:all <none> 2.7.2-4ubuntu1.2
2018-04-03 14:14:30 install nut-monitor:all <none> 2.7.2-4ubuntu1.2
2018-04-03 14:16:28 install libupsclient4:amd64 <none> 2.7.2-4ubuntu1.2
2018-04-03 14:16:28 install nut-client:amd64 <none> 2.7.2-4ubuntu1.2
2018-04-03 14:16:28 install nut-server:amd64 <none> 2.7.2-4ubuntu1.2
2018-04-03 14:16:28 install nut:all <none> 2.7.2-4ubuntu1.2
2018-04-23 09:48:45 install linux-image-4.13.0-39-generic:amd64 <none> 4.13.0-39.44~16.04.1
2018-04-23 09:48:46 install linux-image-extra-4.13.0-39-generic:amd64 <none> 4.13.0-39.44~16.04.1
2018-04-23 09:48:50 install linux-headers-4.13.0-39:all <none> 4.13.0-39.44~16.04.1
2018-04-23 09:48:53 install linux-headers-4.13.0-39-generic:amd64 <none> 4.13.0-39.44~16.04.1

```

to see the names of the most recently installed pkgs does not show them.

I wasn't paying much attention to this as after a decade of being a Linuxer (is that a word?) I thought this was a routine upgrade.  

Where are those 6-8 upgrades? Why are they not listed as "recent", per the above?

---

### Post by Butthead on 2018-04-24
Hi Mark,

Sounds similar to the problems I'm having.  Let me know if you find any fixes for it.  Thanks!

---

### Post by Dennis N on 2018-04-24
> Where are those 6-8 upgrades? Why are they not listed as "recent", per the above? 
With **[FONT=Courier New]grep " install " /var/log/dpkg.log[/FONT]**,  the string " install " only occurs in lines for packages to be newly-installed, not upgraded packages. You could remove the spaces inside the quotes and get the upgraded packages too. Or grep using the date.

---

### Post by Mark_in_Hollywood on 2018-04-25
Thnx for that, Dennis N. I tried to fix the half-installed pulse, pau, alsa and some others but could not restore sound (audio). We are sooo near 18.04LTS, I'm going to wait on that.

---

