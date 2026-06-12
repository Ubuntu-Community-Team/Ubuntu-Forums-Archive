---
title: "[SOLVED] DVD Burning Error - Wrong Media Type"
date: 2008-03-03
forum: General Help
---

### Post by matthewcraig on 2008-03-03
Getting errors on a new spindle of DVD-Rs that I intended to use for burning a large batch of Ubuntu DVD give-aways.

Nautilus gives me a very generic error, but I installed K3B that shows debug information.

```
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
LITE-ON DVDRW SOHW-1633S BS0A (/dev/hda, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Burned media
-----------------------
DVD-R Sequential

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hda obs=32k seek=0'
:-[ PERFORM OPC failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type
/dev/hda: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=0h failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hda=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2220045 -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m 

```

Anyone experience similar issues?  I see many posts in the forum with this error, "Wrong medium type", but I do not see any resolutions.

Thanks in advance.

---

### Post by logos34 on 2008-03-03
It says your drive supports dvd-r, so that's not it.  And growisofs is supposed to automatically format new discs before burning.  Hmm.

Try it manually from the terminal:

**dvd+rw-format -blank /dev/dvd **
(to format the disc.  May need to install **dvd+rw-tools** pkg)
[B]
growisofs -speed=4 -dvd-compat -Z /dev/dvd=yourubuntudvd.iso[/B]

---

### Post by matthewcraig on 2008-03-03
Thanks for your response.  The commands did not have any success.  Here is their output.

```
userme@salamander:~$ dvd+rw-format -blank /dev/dvd 
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
:-( mounted media doesn't appear to be DVD±RW, DVD-RAM or Blu-ray

userme@salamander:~$ growisofs -speed=4 -dvd-compat -Z /dev/dvd=ubuntu-7.10-dvd-i386.iso 
Executing 'builtin_dd if=ubuntu-7.10-dvd-i386.iso of=/dev/dvd obs=32k seek=0'
:-[ PERFORM OPC failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type
/dev/dvd: "Current Write Speed" is 4.1x1352KBps.
:-[ WRITE@LBA=0h failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type
```

---

### Post by logos34 on 2008-03-03
correction: only virgin dvd+rw needs to be formatted.

But you should be able to write to -r with second.

Faulty media? What make (memorex is the worst)?
(k3b>Device>media info)

---

### Post by matthewcraig on 2008-03-03
Media info says, "DVD-R Sequential,  DAXON016S, ... Empty: yes, Layers: 1, ..."

This media is not the best - I bought a spindle of 100 for $30.  But I have tried 10 discs so far, and none work.  I have burned many DVDs from ISOs in the past, because I install Ubuntu through a DVD-R on every release.  You think all these discs are faulty?  Are they all garbage?

I am finding this hard to believe because none of the burning software actually reads the disc before it errors!  I never see the activity light illuminate.

---

### Post by matthewcraig on 2008-03-03
This information here is the best I info I have seen so far in my research:
[http://club.cdfreaks.com/f86/nd-6650a-daxon016s-206909/](http://club.cdfreaks.com/f86/nd-6650a-daxon016s-206909/)

Basically says, Some recorders refuse to deal with certain DVD media brand names.
This does explain why the disc does not need to be read again to be rejected, since that information is read when the disc is inserted.
The software sees the disc is good, but, when it tries to use it, then the recorder says, "no way!"

The link does provide information for hacking the firmware.

---

### Post by logos34 on 2008-03-03
Yeah, I think it may be a brand-related issue (obviously the whole pack can't be faulty) or else a problem with dvd-r format, which from what I gather after googling around a bit seems to cause more problems in linux.  I strictly use DVD+RW and CD-RW.  Wish I could narrow this down for you or suggest an alternative.  But using a different gui isn't going to matter I think, since they all are just frontends for the growisofs command.

---

### Post by matthewcraig on 2008-03-03
Anyway, thanks for your help, logos34

This is very disappointing, because I won't be able to give away the Ubuntu discs, as I hoped, but I will mark this thread as solved because the resolution does seem to appear correct.

---

### Post by Abdi110 on 2008-04-03
Hello. I'm encountering the same error for the past month, all of a sudden. The difference with me is I'm using blanks from the exact same spool of DVDs that were working a month ago.

I have a Lite-On DVD burning in my server, and an identical Lite-On as an external usb. Both are getting the Wrong Medium Type error.

Since the medium is exactly the same, I've got the feeling something "changed" since it last worked, maybe an update?

---

### Post by anthony_barker on 2008-05-06
I have exactly the same problem. Lite-On SOHW-1633S

WRITE@LBA=0h failed with SK=2h/ASC=30h/ACQ=05h]: Wrong medium type

Memorex Gold media works, Silver Memorex DVD-R aand TDK DVD-R give the error.

However I got it working on 2 disks... Strange stuff.

---

