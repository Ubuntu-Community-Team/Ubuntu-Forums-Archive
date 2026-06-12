---
title: "Netbook &quot;sealed&quot;: unable to mount"
date: 2017-08-17
forum: General Help
---

### Post by uxvc on 2017-08-17
Hi, everyone. 
I'm stuck with this.
Well, this old netbook...with 2 OS installed: Windows 7 & Linux Mint.
One day, windows failed to boot. I tried everything, and nothing worked. So I tried to save some things there with Linux, 
then suddenly: 

error: hd0 read error
grub rescue-



I use live-usb-install, with an ubuntu 10.04
Problems with NTFS, so I format the USB in FAT32.

Running ubuntu from my USB give me access to some part of the netbook (a data folder) but I don't have access to windows.
 

[I]Error mounting: mount exited with exit code 13: 
ntfs_attr_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run[/I]*chkdsk*[I] /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the '[/I]*dmraid*[I]' documentation
for more details.[/I]



Tried a few guides...using sudo ntfsfix /dev/sXXX, but doesn't  work.
Any help will be -really- appreciated. 



PS Sorry for the grammar -_-

---

### Post by oldos2er on 2017-08-17
I think you'd need to boot from your Windows installation medium and let it chkdsk its partition, but I'm not a Windows user so it'd be best if you ask this on a Windows forum.

---

### Post by VMC on 2017-08-17
Sounds like a hard drive error. If you can get to a linux terminal (dvd disk), then run smart disk:
[COLOR=#2E8B57][FONT=Monaco]"sudo smartctl -a /dev/sda"[/FONT][/COLOR]

---

### Post by uxvc on 2017-08-17
Thanks for the replies.

well, I can only run it from the usb stick. Looks like the smart disk doesn't work.


Just now there's a warning about errors in a lot of sectors.
This looks bad. Any chance to repair or check the hard disk, running ubuntu from the usb?

---

### Post by oldos2er on 2017-08-17
I don't think any Linux distro can repair

```
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware.
``` That's why you need a Windows medium.

---

### Post by uxvc on 2017-08-17
Ok. Thanks...what a mess.

I think i'm gonna try to find if I can repair somehow the Grub. 
[COLOR=#000000]I was stuck with the *error: hd0 read error *before trying the ubuntu stick.


[/COLOR]

---

