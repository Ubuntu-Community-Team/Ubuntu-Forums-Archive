---
title: "K3b problem! please help"
date: 2007-02-14
forum: General Help
---

### Post by delta99 on 2007-02-14
hello, can someone please help me? 

I've tried now for a few days to copy a disc with k3b. It does not matter what disc, whether it be a CDR data, DVDR data, movies  etc NONE will work.

It creates the image fine. But when the it copies the image it says "Unable to eject media". I searched google, I been to loads of pages and came to the suggestion of root permisions.

SO I tried

```
kdesu k3b
```

I typed in my password and it launched k3b, I tried again to copy a disc but I get the same error "unable to eject media".

I honestly don't know what to do now, can someone please help me? I'm begging you :sad: 

I also try:

```
kdesu k3bsetup
```

The Result =
```
delta@delta-desktop:~$ kdesu k3bsetup
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kcmshell (kdelibs): WARNING: Could not find module 'k3bsetup2'.
delta@delta-desktop:~$ 

```

---

### Post by Shay Stephens on 2007-02-14
I occasionally get the error that it can't eject the disk.  So I just reach over and press the eject button on the drive, and then again to have the disk load back in again to continue doing what it was trying to do.

---

### Post by Niamor on 2007-02-14
To make it work just right click on the icon on the desktop and tell him to unmount the cd/dvd then you can copy iin k3b.

It's a known bug I hope it's gonna be fixed for feisty : [https://launchpad.net/bugs/65907](https://launchpad.net/bugs/65907)

---

### Post by OBnascar on 2007-02-14
Or.........

just install GnomeBaker:

application for CD/DVD creation in the GNOME desktop
Gnomebaker is an easy to use CD/DVD burner. Its current features include:
  * Data and audio CD burning
  * Multisession CDs
  * DVD formating
  * DVD data disk burning
  * On-the-fly data CD burning
  * Cue bin data CD writing

---

### Post by delta99 on 2007-02-14
Hey thanks guys! Appreciate the replies :)

Thank god its a known bug, shame really, but oh well! k3b is still good :D

I also found a work-around... If you tick "create image only", then after the copy the image appears in the list ready to burn. Although its cheap way, it still works for the time being!

thanks again for helping :) I might just look into GnomeBaker.

---

### Post by Shay Stephens on 2007-02-14
gnomebaker does not have data verification.

---

### Post by kinson on 2007-02-21
I tried GnomeBaker a week ago, and I wasn't impressed. No data verification, and I couldnt open the folder that I had added to the explorer in GnomeBaker(??).

I'm going back to K3B :p

---

