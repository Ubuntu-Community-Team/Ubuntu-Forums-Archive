---
title: "Attempting to install 32-bit drivers on 64-bit Ubuntu"
date: 2012-10-23
forum: General Help
---

### Post by Laize on 2012-10-23
I've been wrestling with a wireless adapter the last few days and the only thing I can think of is that perhaps it requires 32 bit drivers rather than 64 bit.  However every attempt I've tried to build the Broadcom STA 32-bit drivers (Which are the correct drivers for my card.  I've checked eleventy billion times.) meets with a similar error to this.

$ make
```
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`

make[1]: Entering directory `/usr/src/linux-headers-3.2.0-32-generic'

Wireless Extension is the only possible API for this kernel version

Using Wireless Extension API

  LD      /media/MOT/hybrid_wl/built-in.o

  CC [M]  /media/MOT/hybrid_wl/src/shared/linux_osl.o

  CC [M]  /media/MOT/hybrid_wl/src/wl/sys/wl_linux.o

/media/MOT/hybrid_wl/src/wl/sys/wl_linux.c:388:2: error: unknown field ‘&#128;&#34152;do_set_multicast_list’&#128;&#12539;specified in initializer

/media/MOT/hybrid_wl/src/wl/sys/wl_linux.c:388:2: warning: initialization from incompatible pointer type [enabled by default]

/media/MOT/hybrid_wl/src/wl/sys/wl_linux.c:388:2: warning: (near initialization for ‘&#128;&#12539;l_netdev_ops.ndo_validate_addr’&#128;&#12539; [enabled by default]

make[2]: *** [/media/MOT/hybrid_wl/src/wl/sys/wl_linux.o] Error 1

make[1]: *** [_module_/media/MOT/hybrid_wl] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'

make: *** [all] Error 2

```

---

### Post by ~LoKe on 2012-10-23
Which card?  That package won't compile with your current kernel.  Have you tried installing it from the repos?
```
sudo apt-get install firmware-b43-installer
```

---

### Post by Laize on 2012-10-23
Everything I can find suggests the BCM4321 requires the Broadcom STA drivers.  What's more I've tried both B43 and STA in 64-bit and been hammering at it for a full day now with chili on the networking board.  It got to the point where everything in the readouts was giving a green light but the card just wouldn't work.  Gas in the engine, it's getting air and the spark plugs firing but the engine just won't turn over.

The only thing I can think of is that it requires a 32-bit driver (The card IS quite old) but I can't seem to get a set of drivers besides the ones off Broadcom's site... which won't build.

---

### Post by ~LoKe on 2012-10-23
I assume you've already seen this thread?
[http://ubuntuforums.org/showthread.php?p=5636495](http://ubuntuforums.org/showthread.php?p=5636495)

---

### Post by Laize on 2012-10-23
> **~LoKe said:**
> I assume you've already seen this thread?
[http://ubuntuforums.org/showthread.php?p=5636495](http://ubuntuforums.org/showthread.php?p=5636495)

Yes I've seen that thread.

Getting the 64-bit drivers is simple.  I can get those straight from the repos.  Neither the b43 or STA drivers work, however.

Like I said, my last recourse is trying 32-bit drivers.  What I'm currently trying to do is follow that thread to install the 32-bit drivers.  Those are the drivers I'm attempting to build in this thread.

---

### Post by Laize on 2012-10-23
> **lawrengary said:**
> It got to the point where everything in the readouts was giving a green light but the card just wouldn't work.[img]<snip>[/img]

In short, neither I nor anyone else on the Networking forum could find anything wrong with my diagnostics.  By all accounts the thing SHOULD have been working.

---

### Post by ~LoKe on 2012-10-23
> **Laize said:**
> In short, neither I nor anyone else on the Networking forum could find anything wrong with my diagnostics.  By all accounts the thing SHOULD have been working.

Networking has always been a pain in the ***.  Have you tried the card on another system?

---

### Post by Laize on 2012-10-23
> **~LoKe said:**
> Networking has always been a pain in the ***.  Have you tried the card on another system?

Yes.

The rig is a straightforward Windows setup.  All the hardware is good.  I've installed Ubuntu 12.04 on a high speed USB drive and used VirtualBox to update libraries/packages/install certain programs I need/etc.

I mainly run it on its own.  I don't run it in the VB unless I have to.  That's why I need the wireless to work so badly.  I don't have direct access to a hard connection, even temporarily.

As I've said I've gone over pretty much everything I can think of that would prevent the NIC from working aside from using 32-bit drivers.

---

### Post by ~LoKe on 2012-10-23
I can't think of anything.  I'm going to download the 32bit drivers and see if I can get them to compile.

---

### Post by ~LoKe on 2012-10-23
Look in src/wl/sys.  Open wl_linux.c and look for 
> .ndo_set_multicast_list = wl_set_multicast_list,

Replace it with:
> .ndo_set_rx_mode = wl_set_multicast_list,

---

### Post by Laize on 2012-10-23
Stupid question.  /src?

It's not in the root dir.

EDIT:  Nevermind I see what you're talking about.

I'm assuming I still need the ia32 libs right?

---

### Post by Laize on 2012-10-23
Did the change you instructed.  Still can't compile.

---

### Post by ~LoKe on 2012-10-23
> **Laize said:**
> Did the change you instructed.  Still can't compile.

Are you getting a different error now?  Probably the same one I am...

> ld: Relocatable linking with relocations from format elf32-i386 (/home/n0c/sta/lib/wlc_hybrid.o_shipped) to format elf64-x86-64 (/home/n0c/sta/wl.o) is not supported


---

### Post by ~LoKe on 2012-10-23
Curious...before going through all this effort, have you tried booting up a 32Bit Live CD?  You'd be able to test if the driver even solves your issue.

---

### Post by Laize on 2012-10-23
That is an excellent idea... I'm glad someone pointed it out to me.

Sorry I've been up for ... a long time trying to fix this.

---

### Post by ~LoKe on 2012-10-23
> **Laize said:**
> That is an excellent idea... I'm glad someone pointed it out to me.

Sorry I've been up for ... a long time trying to fix this.

Don't worry, I've been in your shoes.

---

### Post by Laize on 2012-10-23
> **~LoKe said:**
> Don't worry, I've been in your shoes.

And by the way, yes, the error is the same.

Downloading a 32-bit client right now.  Here's hoping.

---

### Post by Laize on 2012-10-23
Still can't build these darn drivers even on a live 32 bit CD

---

