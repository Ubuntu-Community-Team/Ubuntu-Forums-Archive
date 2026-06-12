---
title: "No sound in Hardy"
date: 2008-06-20
forum: General Help
---

### Post by Lupurus on 2008-06-20
I got things working in Gutsy, but the upgrade to Hardy killed all my sound. I'm not muted anywhere, and alsa seems to be working fine. However, in alsamixer and sound control I only have one channel, PCM.
I have a Toshiba Satellite laptop, but being I noob I don't remember how to check my soundcard.
Any ideas?

---

### Post by cmnorton on 2008-06-21
I had to do this in 7.10, but did not have to in 8.04. 

[http://ubuntuforums.org/showthread.php?t=824958&highlight=alsa+cmnorton](http://ubuntuforums.org/showthread.php?t=824958&highlight=alsa+cmnorton)

---

### Post by gator64 on 2008-07-03
> **Lupurus said:**
> I got things working in Gutsy, but the upgrade to Hardy killed all my sound. I'm not muted anywhere, and alsa seems to be working fine. However, in alsamixer and sound control I only have one channel, PCM.
I have a Toshiba Satellite laptop, but being I noob I don't remember how to check my soundcard.
Any ideas?
I have a Toshiba Satellite A65 and had the same problem. 

To check which sound card you have, you might want to try

```
lspci
```

I have this:
```
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
```

What worked for me was the following:
```

sudo gedit /etc/modprobe.d/alsa-base
```

At the end of the file I added a line saying:
```

options snd-atiixp 
```

Then restart computer.  In sound preferences put everything on Alsa.  Worked for me - your mileage may vary.

---

### Post by Lupurus on 2008-08-04
Hey gator!
I had totally given up on this question getting answered... A little too soon I guess!

The solution didn't work for me, but it's definitely encouraging that you had a similar problem and solved it.

Anyway, lspci tells me:

 Audio device: ATI Technologies Inc SBx00 Azalia

So maybe the solution can be adapted accordingly?

Thank you!
-Lupurus

---

### Post by gator64 on 2008-08-04
Well nothing comes to mind now - maybe you could try the solutions in this thread : [http://ubuntuforums.org/archive/index.php/t-570442.html](http://ubuntuforums.org/archive/index.php/t-570442.html)

Good luck !

---

### Post by else_au on 2008-08-26
I had this problem with my toshiba tecra laptop.  I just "fixed" it and wanted to post my solution.

I saw a number of threads and bugs listing workarounds like:

1) force reloading alsa modules
2) /etc/init.d/alsa-tools reset
3) using the current rt kernel
4) using a more recent (vanilla) kernel than shipped with ubuntu hardy
5) using an older hardy kernel
6) variously toggling output options with alsamixer

There were some others i came across, but those were the most common.  I tried all of these but the older hardy kernel, including rolling my own 2.6.26 kernel package.  None of them worked.

In the end to fix this i added the gutsy repositories and installed the following packages:
linux-headers-2.6.22-14-generic
linux-image-2.6.22-14-generic
linux-ubuntu-modules-2.6.22-14-generic

Then i rebooted.

After logging in, i ran gnome-volume-control and launched mplayer to play an mp3.  Nothing happened at first, so i ran 'sudo /etc/init.d/alsa-tools reset' and immediately sound came out.

I also found that i needed to turn up the "front" volume control in gnome-volume-control.  I also had to mute it to make sound come out just the headphone jack instead of the inbuilt speakers.

I spent hours working on this problem, so I hope this helps a few people out.

---

