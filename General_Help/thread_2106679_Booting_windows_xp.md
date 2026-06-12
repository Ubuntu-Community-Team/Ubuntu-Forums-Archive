---
title: "Booting windows xp"
date: 2013-01-19
forum: General Help
---

### Post by maxalman on 2013-01-19
Recently Mikewhatever helped me fix a duel booting problem I had, I would like to fix one more minor problem if possible. When I turn on my laptop I get the purple screen with option to select Ubuntu +2 more and Windows XP. When I click on windows xp my laptop does not boot windows straight up like it used to it goes to another screen that says please select operating system to start, windows xp home edition, windows default. Any help would be much apreciated.
Alan

---

### Post by sudodus on 2013-01-19
You probably have a file called

```
C:\boot.ini
```

Edit that file (when booted into Windows). There should be a few lines in it that correspond to the alternatives in your second screen with boot choices. If necessary, you can browse to find more help about it on the internet.

---

### Post by maxalman on 2013-01-19
> **sudodus said:**
> You probably have a file called
 
```
C:\boot.ini
```
 
Edit that file (when booted into Windows). There should be a few lines in it that correspond to the alternatives in your second screen with boot choices. If necessary, you can browse to find more help about it on the internet.
 
Hi, thanks for replying, below is copy of the boot.ini file as I am a noob would please advise me which text I should take out.
 
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
 
Edit: I took out noexecute=option but that made no difference.

---

### Post by sudodus on 2013-01-20
> **maxalman said:**
> Hi, thanks for replying, below is copy of the boot.ini file as I am a noob would please advise me which text I should take out.
 
```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
 
Edit: I took out noexecute=option but that made no difference.
```
I would change the timeout setting from 10 seconds to 1 or 0 seconds. But before editing, please make a backup copy of the file. And do the editing when booted into Windows. See this link (or other similar ones) to get more help

[http://best-windows.vlaurie.com/boot-ini.html]("http://best-windows.vlaurie.com/boot-ini.html")

*Edit*: And also remove /noexecute=optin (as you already tried)

---

### Post by maxalman on 2013-01-20
> **sudodus said:**
> I would change the timeout setting from 10 seconds to 1 or 0 seconds. But before editing, please make a backup copy of the file. And do the editing when booted into Windows. See this link (or other similar ones) to get more help
 
[http://best-windows.vlaurie.com/boot-ini.html](http://best-windows.vlaurie.com/boot-ini.html)
 
*Edit*: And also remove /noexecute=optin (as you already tried)
 
Thanks for repling, I saved a backup copy of the file as you advised and changed the time out to 0 and it worked no more having to select my operating system.
Should I need to use the backup copy, how do I go about restoring it.
Thanks Alan

---

### Post by sudodus on 2013-01-21
> **maxalman said:**
> Thanks for repling, I saved a backup copy of the file as you advised and changed the time out to 0 and it worked no more having to select my operating system.
Should I need to use the backup copy, how do I go about restoring it.
Thanks Alan

You should have

- a backup image of the whole drive or

- a restore point (which should contain your boot.ini and its backup) plus a recovery CD of Windows
- a backup image or copy of your Ubuntu /home directory or partition

or at least a backup copy of your personal files (pictures, documents etc)

But specifically: You can boot the computer from Ubuntu or from a CD/USB drive (with Ubuntu or some other linux distro). Then mount the partition with Windows and move or copy the backup file to

```
C:\boot.ini
```
which is called something else in linux for example
```
/media/sda1/boot.ini
```

---

### Post by maxalman on 2013-01-21
> **sudodus said:**
> You should have

- a backup image of the whole drive or

- a restore point (which should contain your boot.ini and its backup) plus a recovery CD of Windows
- a backup image or copy of your Ubuntu /home directory or partition

or at least a backup copy of your personal files (pictures, documents etc)

But specifically: You can boot the computer from Ubuntu or from a CD/USB drive (with Ubuntu or some other linux distro). Then mount the partition with Windows and move or copy the backup file to

```
C:\boot.ini
```which is called something else in linux for example
```
/media/sda1/boot.ini
```

Many thanks for all your help very much appreciated.
Alan  :grin:

---

### Post by sudodus on 2013-01-21
You are welcome :-)

---

