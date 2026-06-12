---
title: "Ubuntu 16.04 Stuck in bootup, cannot make new installation nor run boot-repair iso"
date: 2016-12-28
forum: General Help
---

### Post by harry947 on 2016-12-28
[U][I]This was my computer's condition before
[/I][/U]
I was having some gpu driver problems so, just like every time, I googled. 
I ran lots of commands in the tty1 and terminal and now I'm stuck.

At first, tty1-6 got black but tty7 worked. Then I noticed at bootup, I got the error: No video mode Activated
Below this error: Invalid video mode specification 'none' 
And then
Booting in blind mode
*_After these errors, ubuntu was able to boot but with messed with graphics and at 680x480_*

[B]
This is the current scenario[/B] 
Ubuntu is no longer working, before bootup, I'm asked what I want to do(sytem settings, normal boot, etc). 
Then I get only these errors:
[I]
error: Invalid video mode specification 'none'
Booting in blind mode[/I]

But it never boots(its stuck there)


[B]

These are my specs and what I currently tried [/B]
i3220, GT 730, 8gb ram, 200gb HDD, Ubuntu 16.04, gigabyte mobo 

[LIST=1]
[*]*Currently I've tried *using the boot-repair boot disk(usb) but no matter what I do, it doesn't boot(I have the iso). 
[*]I still have my original ubuntu installation copy(usb), so I'm doing all that I am doing :D through it. 
[*]I tried installing a nvidia driver(using my installation copy) which I manually downloaded, I successfully *stopped lightdm*, *blacklisted nouveau, *but still during installation nvidia(installer) told me to disable nouveau kernel. 
[/LIST]
      4. I tried reinstalling grub(mounting my partitions,etc) but I got this error:
[I]Fatal Python error: Py_Initialize: Unable to get the locale encoding
ValueError: source code string cannot contain null bytes

Current thread 0x00007f4f121be700 (most recent call first):
Aborted (core dumped)
[/I]
I created the bootable usb in (1) using startup disk creator(ubuntu), I tried installing other softwares but was unsuccessful in getting them to make a proper bootable pendrive

Thanks
PS Guys I tried reinstalling ubuntu, but during the actual installation I get the error "input/output" error cannot install ubuntu

Update: was able to install boot-repair onto the liveusb but during repair I got this error: *Please enable a repository containing the [grub-efi-amd64-signed] packages in the software sources of Ubuntu 16.04.1 LTS (sda2)*
This is boot-repair info: [http://paste2.org/py6eV5Oe](http://paste2.org/py6eV5Oe)

---

### Post by harry947 on 2016-12-28
Update: Guys, I use able to run boot repair from the liveusb, but soon after it began, Ubuntu froze.
Later I got this: [[img]https://s23.postimg.org/ivqdi5gpj/IMG_20161228_172803.jpg[/img]](https://postimg.org/image/ivqdi5gpj/)

---

### Post by mörgæs on 2016-12-30
Have you tried a fresh install of 16.10?

---

### Post by harry947 on 2017-01-09
Yes tried to do that too, but input/output error. 
Infact I even tried update ubuntu from terminal using the && command(sorry forgot the command) but no lucky :/

---

### Post by mörgæs on 2017-01-09
> **harry947 said:**
> Yes tried to do that too, but input/output error. 


Please post the exact wording. Could be a hard disk problem.

---

