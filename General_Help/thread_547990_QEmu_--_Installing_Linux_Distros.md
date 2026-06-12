---
title: "QEmu -- Installing Linux Distros"
date: 2007-09-10
forum: General Help
---

### Post by xMemphisx on 2007-09-10
Alright, i'm trying to use QEmu to install another operating system (possibly a few more) that i can use. I tried installing BackTrack, but it wanted to change the MBR... i just wanted to make sure that if i DID go ahead and install it... it wasn't actually going to affect the MBR at all... and also, how can i pick a HDD when it's running virtually? I don't want to say, /dev/sda1, because that's where Ubuntu is currently installed. Any info on this stuff would be greatly appreciated.

---

### Post by bodhi.zazen on 2007-09-10
qemu uses virtual hard drives, or qcow files by default ...

so ...

qemu .... -hda ubuntu.qcow ... and on ...

Here is a nice overview of how to qemu :

[uwiki]WindowsXPUnderQemuHowTo[/uwiki]

You might also want to check out some of the gui front ends for qemu, like : qemu-launcher

```
sudo apt-get install qemu-launcher
```

Although there are others ...

=====

To answer you original question, no when installing an OS onto a virtual drive , the MBR is on the virtual drive as well.

This is a longer qemu manual if you lilke : 

[http://fabrice.bellard.free.fr/qemu/qemu-doc.html](http://fabrice.bellard.free.fr/qemu/qemu-doc.html)

---

### Post by diatribe on 2007-09-10
unless you specifcally tell the program to either share folders or use your physical drive, a virtual machine can not affect your actual drives

---

