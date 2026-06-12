---
title: "Need help unbreaking my boot - Fresh ubuntu install"
date: 2018-05-13
forum: General Help
---

### Post by weiry6922 on 2018-05-13
So the title basically says it all. I've got myself into a bit of a situation where I cannot boot into my fresh install system at all. I can only guess it has something to do with my booting not being setup correctly.

I am attempting to install Ubuntu 17.10.

What's happening:

- I turn on PC
- Get a message that I can't read in time, something along the lines of: System BootOrder not found. Initializing defaults.
- PC restarts
- Endless loop

What I've tried:

- Complete fresh install with Ubuntu live usb
- Boot in with live usb and use gparted to try and set some stuff up
- boot-info - [http://paste.ubuntu.com/p/gSSdkpVfxt/](http://paste.ubuntu.com/p/gSSdkpVfxt/)

What I done leading up to this:

- PC was originally a Windows 10 install
- I removed Windows 10 to try Arch Linux
- I am now trying to install Ubuntu deleting my old Arch Linux installation

Like I said, I believe I've messed up my booting and I am completely unsure how to fix it. It says something down the bottom of boot-info about making my BIOs boot from a different efi but I can't find where to change it. I am running a ThinkPad T470s.

Some side questions:

I'm doing this as a practice exercise before I do it on my main PC. I want to install a Arch linux OS alongside my existing Ubuntu installation. Do I have the steps to do this correct? Is there anything I'm missing?

- I have 2 partitions one is with 500mb and the other has the rest of my GBs (boot and filesystem?)
- I boot the pc with a live CD, unmount the partition with all of my space (filesystem?)
- Shrink the unmounted partition and then remount it
- Now I install Arch linux on the space that I've free'd up from the shrinking?

Any help would be greatly appreciated. Thanks.

E: [In case anyone else ever runs into this issue, this was the fix]("https://askubuntu.com/questions/862946/unable-to-install-ubuntu-on-acer-aspire-es1-533/876153#876153")

---

### Post by dino99 on 2018-05-13
Try to get a tty console (ctrl+alt+F2) and post the output of 'journalctl -b > journal.txt'

---

### Post by weiry6922 on 2018-05-13
I can boot into Ubuntu live USB and get the output of that if that would work?

---

### Post by dino99 on 2018-05-13
Was asking about the real install, not a live usb one which is pointless of course.

---

### Post by weiry6922 on 2018-05-13
Yeah thought so :)

Don't think it will be possible, the message is the first thing that comes up

---

### Post by kazakore on 2018-05-13
Sounds like an EFI problem to me.

Press whatever button you need to get Boot Option. Select EFI Path (or similar.) You are looking for something like:
/EFI/ubuntu/grubx64.efi

To not have to do this every time you have to add this as a Custom Boot in the BIOS.


EDIT Sorry I somehow missed it was SOLVED already :)

---

