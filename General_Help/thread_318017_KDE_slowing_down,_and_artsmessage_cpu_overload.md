---
title: "KDE slowing down, and artsmessage cpu overload"
date: 2006-12-13
forum: General Help
---

### Post by mirshafie on 2006-12-13
Since I installed Kubuntu Edgy, I've had som bad problems with KDE slowing down after different periods of time. Sometimes it's an hour, sometimes ten, but it always happens. Suddenly, everything just goes slower and slower until I'm thrown out, back at kdm (unless I logout first).

I cannot see that this should be a problem with any of the applications I regularly run (Konqueror, amaroK, KTorrent, Konversation, Kopete, yakuake, Akregator, KAlarm, IRkick, Firefox). They do not seem to consume unusual amounts of CPU or RAM, according to top (not even Firefox! :p ).

There's another problem, which could be related. Sometimes when I run MPlayer, I'm suddenly kicked back at kdm, and sometimes I get the following error dialog:

[INDENT]Error - artsmessage

Sound server fatal error:

cpu overload, aborting
[/INDENT]

Most of the time it works fine though.

I have no idea what to do about this, I've never had any problems like this with before. It worked fine when I upgraded from Dapper by altering the sources.list, but I had booting problems then (apparently I wasn't the only one).

I hope you people can help me with this, it's killing me. I'm seeing nighttime visions of Windows XP with Norton AV and foobar2k, and it's awful, you have to save me from this mess!

Thanks! :mrgreen:

---

### Post by mojorising on 2006-12-23
I get the same error message after upgrading from dapper to edgy. KDE does not slow down though. Not sure what this is.

Mike

---

### Post by Bogolt on 2007-01-02
the same happends to me with Ubuntu Edgy when i start Kopette. And this  happends only on x86 version of Ubuntu. Kopette is running ok on 64 bit version.

---

### Post by Ubuntiac on 2007-01-24
Ditto here.

I also get all sound working fine on about  50% of bootups and no sound at all on 50%.

Wierd.

This is also a new problem for me since upgrading from dapper to edgy. We have another computer that runs just fine.

---

### Post by zer0skill on 2007-03-14
6.10 Edgy...

Linux zer0skill 2.6.17-11-generic #2 SMP Thu Feb 1 18:03:05 UTC 2007 x86_64 GNU/Linux

 7783 root      25   0 54444 9184 6584 R 95.8  0.7   6:13.67 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -l 3 -f

What could possibly be going on?

No applications running that use sound.... 

Repeated CPU OVERLOAD messages get really annoying.

---

### Post by konungursvia on 2007-03-14
SWitch to gnome.

---

### Post by jetpeach on 2007-03-24
getting the same message here. anybody found a solution? here's somebody else having the problem as well
[http://www.ubuntuforums.org/showthread.php?t=385642&highlight=cpu+overload+sound](http://www.ubuntuforums.org/showthread.php?t=385642&highlight=cpu+overload+sound)
there are many threads on this but i can't find any answers

found this bug
[https://launchpad.net/ubuntu/+source/arts/+bug/66982](https://launchpad.net/ubuntu/+source/arts/+bug/66982)
and the problem was fixed for me anyway by typing
echo "options snd-via82xx dxs_support=2" |sudo tee -a /etc/modprobe.d/alsa-base

---

### Post by Takmadeus on 2007-04-09
Well i must say that I have the same problem, but I am currently using gnome just that I got some kde apps, but I think that would be all

---

