---
title: "Odd Issue. Can't play DVDs."
date: 2007-02-19
forum: General Help
---

### Post by Roasted on 2007-02-19
I've got this live concert on DVD of Nirvana, and I was just trying to play it. When I go to play it, nothing opens. Everything opens by "open folder" and not a program. I navigated to the video files and clicked on the first one. It played in VLC. Okay fine. But after that one ended, it didn't start the 2nd clip. So I tried to start the 2nd clip manually, and it turned from .vob into a text file. What in the world? 

Essentially I need to know how to set up VLC or Mplayer (whichever) to be my default player for any media that is put in my CD rom.

---

### Post by dcstar on 2007-02-21
> **Roasted said:**
> I've got this live concert on DVD of Nirvana, and I was just trying to play it. When I go to play it, nothing opens. Everything opens by "open folder" and not a program. I navigated to the video files and clicked on the first one. It played in VLC. Okay fine. But after that one ended, it didn't start the 2nd clip. So I tried to start the 2nd clip manually, and it turned from .vob into a text file. What in the world? 

Essentially I need to know how to set up VLC or Mplayer (whichever) to be my default player for any media that is put in my CD rom.

If you are using Gnome:

System-Preferences-Removable Drives and Media and select the application you want to use for that type of media.

---

### Post by Roasted on 2007-02-21
If I want VLC to open it, what exactly do I put in? Just putting in VLC will open it, but won't auto-play it. How can I do that?

---

### Post by ~LoKe on 2007-02-21
> **Roasted said:**
> If I want VLC to open it, what exactly do I put in? Just putting in VLC will open it, but won't auto-play it. How can I do that?

```
vlc dvd://
```

---

### Post by Iandefor on 2007-02-21
> **Roasted said:**
> I've got this live concert on DVD of Nirvana, and I was just trying to play it. When I go to play it, nothing opens. Everything opens by "open folder" and not a program. I navigated to the video files and clicked on the first one. It played in VLC. Okay fine. But after that one ended, it didn't start the 2nd clip. So I tried to start the 2nd clip manually, and it turned from .vob into a text file. What in the world? 

Essentially I need to know how to set up VLC or Mplayer (whichever) to be my default player for any media that is put in my CD rom.Have you tried > mplayer dvd://[title] Or is there something funky with your DVD drive?

---

### Post by Roasted on 2007-02-21
Still won't autoplay using the VLC dvd://

---

### Post by Roasted on 2007-02-25
Let me reiterate. It'll open, just not play. Even if I hit play... nothing happens.

Should I have a certain package installed?

---

### Post by Iandefor on 2007-02-25
> **Roasted said:**
> Let me reiterate. It'll open, just not play. Even if I hit play... nothing happens.

Should I have a certain package installed? The odds against it are low, but do you have libdvdcss installed?Try```
sudo aptitude search libdvdcss
``` And post the output.

---

### Post by Roasted on 2007-02-25
jason@jason:~$ sudo aptitude search libdvdcss
Password:
i   libdvdcss2                      - Library for accessing DVDs like block devi
jason@jason:~$

---

### Post by Maestro23 on 2007-02-25
> **Roasted said:**
> jason@jason:~$ sudo aptitude search libdvdcss
Password:
i   libdvdcss2                      - Library for accessing DVDs like block devi
jason@jason:~$

That command searches the repositories... not what is on your system.  Try this:

> locate libdvdcss2

---

### Post by Iandefor on 2007-02-25
> **Maestro23 said:**
> That command searches the repositories... not what is on your system.  Try this:Yeah, but the search indicates if it's installed or not. The "i" at the beginning indicates that it's been installed ;).

---

### Post by Maestro23 on 2007-02-25
> **Iandefor said:**
> Yeah, but the search indicates if it's installed or not. The "i" at the beginning indicates that it's been installed ;).

Ahh.. Thanks, just learned a new little tidbit.:)

---

### Post by Iandefor on 2007-02-25
> **Maestro23 said:**
> Ahh.. Thanks, just learned a new little tidbit.:)Good. So did I: locate [library] is faster than sudo aptitude search [library] if you want to see if you have [library] installed.

---

### Post by Maestro23 on 2007-02-25
> **Iandefor said:**
> Good. So did I: locate [library] is faster than sudo aptitude search [library] if you want to see if you have [library] installed.

Yeah, locate is just concerned about what's on your system. 

That's what I love about linux, more than one way to skin a cat.:lolflag:

---

### Post by Roasted on 2007-02-26
*shrug*



jason@jason:~$ locate libdvdcss2 
/var/lib/dpkg/info/libdvdcss2.shlibs
/var/lib/dpkg/info/libdvdcss2.list
/var/lib/dpkg/info/libdvdcss2.postinst
/var/lib/dpkg/info/libdvdcss2.postrm
/var/lib/dpkg/info/libdvdcss2.md5sums
/usr/share/doc/libdvdcss2
/usr/share/doc/libdvdcss2/copyright
/usr/share/doc/libdvdcss2/README
/usr/share/doc/libdvdcss2/AUTHORS
/usr/share/doc/libdvdcss2/changelog.Debian.gz
/usr/share/doc/libdvdcss2/changelog.gz
/usr/share/doc/libdvdcss2/NEWS.gz
jason@jason:~$

---

### Post by Roasted on 2007-03-01
Okay, found out something new.

I have 2 dvd drives. a DVD-ROM and a DVD-Burner (dual layer).

The DVD-Burner will play the movie using vlc dvd://.
The DVD-ROM will not.

I also tried using "cdrom" and "cdrom0" in place of dvd:// thinking maybe it'd work, but it wouldn't.

Why doesn't my DVD-ROM drive respond to the movie? VLC opens... it just won't play.

---

### Post by maddog39 on 2007-03-01
Do you have IDE or SATA DVD drives? Because depending on your drive type, they will also show up as a standard hard disk. For example, I have 2 SATA hard drives,

/dev/sda      and
/dev/sdb

then my DVD drive is (since its IDE):

/dev/hda

Then in your case, if you have your second drive, it'd be:

/dev/hdb

But if you have, lets say, two hard drives, and two dvd/cd drives both using IDE or SATA, it'd be something like this:

IDE Config:
/dev/hda  - Hard Disk 1
/dev/hdb  - Hard Disk 2
/dev/hdc  - DVD/CD Disk 1
/dev/hdd  - DVD/CD Disk 2

SATA Config:
/dev/sda  - Hard Disk 1
/dev/sdb  - Hard Disk 2
/dev/sdc  - DVD/CD Disk 1
/dev/sdd  - DVD/CD Disk 2

Thats an example layout for both IDE and SATA drives. Those "/dev/sda" or whatever, things, are your physical drive locations in linux. So if you use VLC Player for example, when you choose your disk to play from, enter one of those locations and it will search for a DVD movie.

I just had this same problem and thats how I know, this is the way I found and solved the problem. Hope I make sense and that this helps you some.

-maddog39

[Edit]
If I'm wrong in my examples on how the drives might be layed out, someone correct me.

---

### Post by Maestro23 on 2007-03-01
> **Roasted said:**
> Okay, found out something new.

I have 2 dvd drives. a DVD-ROM and a DVD-Burner (dual layer).

The DVD-Burner will play the movie using vlc dvd://.
The DVD-ROM will not.

I also tried using "cdrom" and "cdrom0" in place of dvd:// thinking maybe it'd work, but it wouldn't.

Why doesn't my DVD-ROM drive respond to the movie? VLC opens... it just won't play.

What is the output of:

> cat /etc/fstab

---

### Post by Roasted on 2007-03-02
jason@jason:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=bc849096-62a5-415a-a0c6-fddda79007cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=343CEEAE3CEE6A76 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=27a1e042-5389-4887-b630-88989d5ca538 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
jason@jason:~$

---

### Post by Maestro23 on 2007-03-02
> **Roasted said:**
> jason@jason:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=bc849096-62a5-415a-a0c6-fddda79007cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=343CEEAE3CEE6A76 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=27a1e042-5389-4887-b630-88989d5ca538 none            swap    sw              0       0
[COLOR="Red"]/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0[/COLOR]
jason@jason:~$

Make sure your media player's prefs/settings is pointed at the correct cdrom. Experiment with either /dev/hda or /dev/hdb .  I had to do the same with mine, finally got it figured out and can play DVDs in all my media players.

---

### Post by Roasted on 2007-03-02
Where would this be in VLC? I've never had to do this before. :(

---

