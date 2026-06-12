---
title: "Equivalent of DaemonTools needed"
date: 2006-12-17
forum: General Help
---

### Post by RobotChild on 2006-12-17
Does anyone know of a Daemon Tools-esqe program for Linux?

I ripped a bunch of my games which used DVDs (My computer running Ubuntu only has a CD-R) and transfered them over to my other computer running Dapper.

I've paid for Cedega, but I cannot figure out how to install the game from an .NRG without mounting it. (Which would let me access the .EXE)

---

### Post by yabbadabbadont on 2006-12-17
Look into the cdemu package.  I believe it does complete cd emulation and supports NRG as well as bin/cue and iso.

---

### Post by RobotChild on 2006-12-17
I couldn't figure out what to do after I extracted it.

Yes, I read the INSTALL thing

---

### Post by taurus on 2006-12-17
Can you just mount it with

Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop filename.nrg /media/iso
ls -la /media/iso
```

---

### Post by yabbadabbadont on 2006-12-17
[http://cdemu.org/](http://cdemu.org/)

They have some (very brief) instructions on their homepage.  I haven't personally used it (yet).  So I can't say how well it works.  I just knew that it existed as it was suggested by one of the entries in the WINE appdb as a workaround for games that come on mixed mode CDs.

---

### Post by yabbadabbadont on 2006-12-17
> **taurus said:**
> Can you just mount it with

Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop filename.nrg /media/iso
ls -la /media/iso
```

NRG files are not ISO files.  You have to use the nrg2iso tool to convert them.  But you can't do that with mixed mode NRG images.

---

### Post by RobotChild on 2006-12-17
As I am still a big Linux noob, I really don't understand the instructions.

---

### Post by RobotChild on 2006-12-17
Could anyone review the instructions for CDEmu and explain what I need to do in layman terms?

[http://cdemu.sourceforge.net/#install](http://cdemu.sourceforge.net/#install)

I'm mostly confused about the first point, and am I supposed to do this all in the Terminal?

---

### Post by po0f on 2006-12-17
RobotChild,

Do all this from the terminal (ignore the dollar sign ($), it represents your terminal prompt):
```
[FONT="Courier New"]$ sudo aptitude update
$ sudo aptitude install build-essential linux-headers-`uname -r`
$ mkdir -p ~/src/cdemu
$ cd ~/src/cdemu
$ wget http://prdownloads.sourceforge.net/cdemu/cdemu-0.8.tar.bz2
$ tar xvjf cdemu-0.8.tar.bz2
$ cd cdemu-0.8
$ make
$ sudo make install
$ sudo modprobe cdemu[/FONT]
```

I don't know how well it actually works, I just now installed it myself.  ;)

---

### Post by MetalMusicAddict on 2006-12-17
> **RobotChild said:**
> I'm mostly confused about the first point, and am I supposed to do this all in the Terminal?

Yes. Currently there is no DaemonTools equivalent on linux. There are ways to do about the same thing but not a easy, all-in-one solution like DaemonTools.

Do you just want to mount a iso? Thats it? Nothing special?

---

