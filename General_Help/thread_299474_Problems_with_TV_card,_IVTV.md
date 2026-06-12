---
title: "Problems with TV card, IVTV"
date: 2006-11-14
forum: General Help
---

### Post by 64mgb on 2006-11-14
There must be something obvious I'm missing.  I can't get my Diamond PVR-560 TV card to work in Ubuntu.  I'm starting with a fresh install of Edgy on a brand new PC with an AMD Athlon 64 3200+ CPU.  After I've installed Ubuntu, the only thing I do then is load IVTV per these instructions:

[https://wiki.ubuntu.com/Install_IVTV_Edgy](https://wiki.ubuntu.com/Install_IVTV_Edgy)

Everything loads up fine and when I do dmesg it shows that it detects and initializes the card, but there is nothing about the tuner module or tveeprom (I'm not at home now so I can't paste in the output from dmesg...I can do that later if anyone wants to see it).  Shouldn't they be started?  I can do "sudo modprobe tuner" and it doesn't give me any errors, but still doesn't show anything about tuner in dmesg.

What am I missing?  By the way, I can put in my cheap Pinnacle TV card and it works fine (well, the video works fine...I have to fiddle with it a lot to get the audio to work).

Thanks,
Rich

---

### Post by 64mgb on 2006-11-15
Bump

---

### Post by superm1 on 2006-12-17
Hi, I just came across your post.  Can you post the output of dmesg still?

---

### Post by 64mgb on 2006-12-17
> **superm1 said:**
> Hi, I just came across your post.  Can you post the output of dmesg still?

Hi superm1 -

I'm still struggling with this.  In the meantime I bought a Hauppauge PVR-150 and it is working fine.  I'm working with the Diamond card in a test box and have tried MANY things to get it working, but no luck yet.  I can across this post regarding the Xceive xc3028 tuner, which my card has:

[http://www.gossamer-threads.com/lists/ivtv/devel/32112](http://www.gossamer-threads.com/lists/ivtv/devel/32112)

I've tried the instructions in that post (including cobbling together a version of videodev2.h that will allow both the v4l tree and the ivtv tree to compile) with no success.

I'm a geek, but a relative newbie when it comes to Linux and C programming (I've always been a Delphi guy), so I'm learning a lot.

I'm currently in the process of starting from scratch (again) because I was at a point that I didn't know for sure what I had where.  Once I have Ubuntu loaded and IVTV loaded, I'll start it up that way and post my dmesg ouput...hopefully within the next hour.

Thanks,
Rich

---

### Post by superm1 on 2006-12-17
> **64mgb said:**
> Hi superm1 -

I'm still struggling with this.  In the meantime I bought a Hauppauge PVR-150 and it is working fine.  I'm working with the Diamond card in a test box and have tried MANY things to get it working, but no luck yet.  I can across this post regarding the Xceive xc3028 tuner, which my card has:

[http://www.gossamer-threads.com/lists/ivtv/devel/32112](http://www.gossamer-threads.com/lists/ivtv/devel/32112)

I've tried the instructions in that post (including cobbling together a version of videodev2.h that will allow both the v4l tree and the ivtv tree to compile) with no success.

I'm a geek, but a relative newbie when it comes to Linux and C programming (I've always been a Delphi guy), so I'm learning a lot.

I'm currently in the process of starting from scratch (again) because I was at a point that I didn't know for sure what I had where.  Once I have Ubuntu loaded and IVTV loaded, I'll start it up that way and post my dmesg ouput...hopefully within the next hour.

Thanks,
Rich
Okay if you get this working, I'll help you get this into a debian package.

---

### Post by 64mgb on 2006-12-17
Here's my dmesg output:

[17180268.208000] Linux video capture interface: v1.00
[17180268.276000] ivtv:  ==================== START INIT IVTV ====================
[17180268.276000] ivtv:  version 0.7.0 (tagged release) loading
[17180268.276000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17180268.276000] ivtv:  In case of problems please include the debug info between
[17180268.276000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17180268.276000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17180268.280000] ivtv0: Autodetected Yuan PG600, Diamond PVR-550 card (cx23416 based)
[17180268.280000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 201
[17180268.552000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17180271.864000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[17180272.608000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17180272.824000] ivtv0: Encoder revision: 0x02050032
[17180272.824000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17180272.828000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17180272.828000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17180272.828000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17180272.936000] ivtv0: Initialized Yuan PG600, Diamond PVR-550, card #0
[17180272.936000] ivtv:  ====================  END INIT IVTV  ====================

Rich

---

### Post by superm1 on 2006-12-17
> **64mgb said:**
> Here's my dmesg output:

[17180268.208000] Linux video capture interface: v1.00
[17180268.276000] ivtv:  ==================== START INIT IVTV ====================
[17180268.276000] ivtv:  version 0.7.0 (tagged release) loading
[17180268.276000] ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[17180268.276000] ivtv:  In case of problems please include the debug info between
[17180268.276000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17180268.276000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17180268.280000] ivtv0: Autodetected Yuan PG600, Diamond PVR-550 card (cx23416 based)
[17180268.280000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 16 (level, low) -> IRQ 201
[17180268.552000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17180271.864000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[17180272.608000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17180272.824000] ivtv0: Encoder revision: 0x02050032
[17180272.824000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17180272.828000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17180272.828000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17180272.828000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17180272.936000] ivtv0: Initialized Yuan PG600, Diamond PVR-550, card #0
[17180272.936000] ivtv:  ====================  END INIT IVTV  ====================

Rich
Rich,
I'll give you a rough over view how you will patch the ivtv packages to include this support as well as how you will grab the linux source, but I won't be able to walk you through the entire process.

You will need dpkg-dev and devscripts.

```
sudo apt-get install dpkg-dev devscripts build-essential
```

You may not need the entire kernel source.  More likely you can work off of a headers package.

You will need to install the buildtime dependencies for ivtv.

```
sudo apt-get build-dep ivtv-source
```

You will need to get the ivtv source

```
apt-get source ivtv
```

You will need to modify the changelog to make sure that this version doesn't conflict with the version on the repositories.

```
cd ivtv-0.7.0
dch -i
```

The first line will become

```
ivtv (0.7.0-3) unstable; urgency=low
```

Change this to be
```
ivtv (0.7.0-2ubuntu0unofficial1) unstable; urgency=low
```

This will guarantee that your version never conflicts with an ubuntu version if we ever release an update.

Patch your package as necessary

to run the build, you will run 

```
dpkg-buildpackage
```

And then install as needed :)

I'm sure you will have questions, and this isn't a complete howto to modifying a package, but it will help you properly patch the sources for ivtv at least so that you can still keep your debian based system cleaner from free floating binaries.

---

### Post by 64mgb on 2006-12-17
Thanks superm1 - 

I'll see if I can stumble through this.  I see you are referring to ivtv 0.7.0, but the ivtv home page says that 0.7.3 is the current version for the 2.6.17 kernel...should I be using 0.7.0?

Rich

---

### Post by superm1 on 2006-12-18
> **64mgb said:**
> Thanks superm1 - 

I'll see if I can stumble through this.  I see you are referring to ivtv 0.7.0, but the ivtv home page says that 0.7.3 is the current version for the 2.6.17 kernel...should I be using 0.7.0?

Rich
I have packaged a later release at the ivtv website that you can grab the debian source for as well (0.7.2 - i'm a release behind in packaging).  I'm not particularly sure on the changes from that release to this one however.
Hopefully I'll get the 0.7.3 packaged soon, which will also be available as a debian package, dl.ivtvdriver.org/ubuntu

---

