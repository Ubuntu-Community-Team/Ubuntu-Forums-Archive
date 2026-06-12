---
title: "Creation of Installation Disk for Ubuntu on Rasberry Pi"
date: 2019-06-08
forum: General Help
---

### Post by Old Jimma on 2019-06-08
Hi Community: ):P

I'm having trouble with creating a bootable Ubuntu image SD Card or USB flash drive so that I can use Ubuntu Core as the opperating sytem on my Rasberri Pi. :confused:](*,)


Instructions for creating a bootable Ubuntu image SD Card are at: [http://www.ubuntu.com/download/iot/installation-media]("http://www.ubuntu.com/download/iot/installation-media")

The image file name is: [COLOR="#008000"]ubuntu-18.04.2-preinstalled-server-arm64+raspi3.img.xz[/COLOR]

... and it is stored in the downloads foler: ~/Downloads/




**[COLOR="#0000FF"]The instructions say: If the Ubuntu image file you have downloaded ends with an `.xz` file extension, run:[/COLOR]**
> xzcat ~/Downloads/ < image file .xz > | sudo dd of=< drive address > bs=32M

**[COLOR="#0000FF"]I used the command:[/COLOR]**
> xzcat ~/Downloads/ < [COLOR="#008000"]ubuntu-18.04.2-preinstalled-server-arm64+raspi3.img.xz[/COLOR] > | sudo dd of=< /dev/sdb > bs=32M

**[COLOR="#0000FF"]and get the bash error message:[/COLOR]**
> bash: syntax error near unexpected token `|'

[B][COLOR="#0000CD"]How do I correct the bash command to work correctly??
[/COLOR][/B]

Thanks! :D
Old Jimma from the Old Country
:guitar:

---

### Post by C.S.Cameron on 2019-06-08
Ubuntu Mate worked for me: [https://ubuntu-mate.org/raspberry-pi/](https://ubuntu-mate.org/raspberry-pi/)

---

### Post by TheFu on 2019-06-08
```
xz --decompress --stdout /path/to/file/ubuntu-18.04.2-preinstalled-server-arm64+raspi3.img.xz |sudo dd of=/dev/sdZ bs=32M

```where sdZ is the specific device for the storage device you want overwritten.

You can also use 2 steps - the ```
xz --decompress /path/to/file/ubuntu-18.04.2-preinstalled-server-arm64+raspi3.img.xz
```
followed by
```
sudo dd if=/path/to/file/ubuntu-18.04.2-preinstalled-server-arm64+raspi3.img of=/dev/sdZ bs=32M
```

But it is up to you.  manpages for the commands explain these things, BTW.
I'd probably use 4M for the blocksize, but whatever.

---

### Post by Old Jimma on 2019-06-08
Dear Fu:

Your advice worked perfectly! I used the 4m block size and all went well!

Next step: Amazon delivers the parts for my Rasberry Pi, I assemble, stick in the card, and boot up.

We'll see what happens next!!

THANKS!

Older than Rocks Old Jimma from the Old Country

---

### Post by TheFu on 2019-06-08
There are much better ARM SBCs than any Raspberry Pi for just a tiny bit more cash.  We're talking about 2x the performance for either the same price or $10 more.

The Pi line is great for the community and lots of software, but the I/O and CPU performance are lacking compared to less popular options.

---

