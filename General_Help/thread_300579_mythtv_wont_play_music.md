---
title: "mythtv wont play music"
date: 2006-11-15
forum: General Help
---

### Post by kamilczauz on 2006-11-15
hey guys, i just installed mythtv per the instructions on this forum, and everything was working a while ago, and now i cant play any music.

I get this error in the terminal.

2006-11-15 22:25:55.951 Opening audio device '/dev/dsp'.
2006-11-15 22:25:55.951 Opening OSS audio device '/dev/dsp'.
2006-11-15 22:25:55.951 WARNING: something is currently using: /dev/dsp, retrying.
2006-11-15 22:25:56.902 Opening audio device '/dev/dsp'.
2006-11-15 22:25:56.902 Opening OSS audio device '/dev/dsp'.
2006-11-15 22:25:56.902 WARNING: something is currently using: /dev/dsp, retrying.


thanks in advanced,
Kamil Czauz

---

### Post by kamilczauz on 2006-11-16
just to add...

its mythtv 0.18 and ubuntu 6.06 dapper

thanks guys

---

### Post by kamilczauz on 2006-11-16
hey... figure out my problem...

if you followed this toturial like i did.. [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) ... then your music wont play.

when you get up to this part

6.3 Finalizing the Installation...

dont follow the instructions. if you add this script

cd /etc/init.d
wget [http://s91928265.onlinehome.us/hfamily/mythtv/mythtv-backend](http://s91928265.onlinehome.us/hfamily/mythtv/mythtv-backend)
chmod a+rx mythtv-backend

your music just wont play... so just remove that script and you should be fine.

kamil

---

### Post by superm1 on 2006-11-17
Just as a shameless plug, you might consider moving up to 0.20.  I Have repos assembled for 6.06.

See [https://help.ubuntu.com/community/MythTV/Install/Server/Dapper/Repositories](https://help.ubuntu.com/community/MythTV/Install/Server/Dapper/Repositories)
For more information about them.

Also, you will probably have more luck with your audio problem by changing the audio device in myth from 
```
/dev/dsp
```
 and 
```
/dev/mixer
``` to

```
ALSA:default
``` for both

---

