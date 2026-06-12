---
title: "How do I flash bios?"
date: 2008-04-16
forum: General Help
---

### Post by Robbyx on 2008-04-16
I have spent hours trying to find ways to upgrade my bios. I have found lots of instructions none of which have worked.

The first stage might be to get my floppy to work.  I have some old floppies that I had hoped to use for the flash upgrade. Under Ubuntu I view the contents and some files are on it. I delete them. Put another disk in and it shows it is empty as well. I have also had it showing files when there is no disk in the drive. 

Here is my fsab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=003e4d16-908b-442c-92a6-9c3578d12c36 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd3  being new "home"
# UUID=f453ce62-336b-490b-8447-55acd2adc952 /home  ext3    nodev,nosuid,user_xattr    0       2
#/dev/sda2  being new "home"
UUID=45a2e92c-c759-4732-9662-988da7f8ea7b /home  ext3    nodev,nosuid,user_xattr    0       2


#records and my docs (rade sdb1)
UUID=724E07853D78E7A8 /media/mydocs ntfs user,auto,noexec 0  2

#old download partition hdb5
UUID=7E0442D704429257 /media/downloads ntfs auto,user 0 0

#media
UUID=b1bba368-3025-45c2-94cd-3ac8a32e40fd /media/flm reiserfs auto,user 0 2


/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto,umsdos,vfat,ext2    rw,user,noauto,exec 0       0
```

Is there anything there that could stop the floppy being properly mounted?


I only have a Win2k. Would the best approach be to put in an old HD and install it and try and flash the bios from it?

I have bought a E8200 and can not run it under gutzy without a bios upgrade, I think.

Robin

---

### Post by kutjara on 2008-04-16
I've had similar problems, and none of the recommended solutions have worked. Even using a boot floppy isn't viable for me, because the BIOS files I need are bigger (even compressed) than a floppy disk can accommodate.

I tried a bootable USB, because my BIOS says it can boot from a USB stick. Guess what? It can't. The USB drive doesn't light up until Ubuntu is well on the way to being fully booted.

I tried various bootable DOS CDs that promised to enable my USB ports, so I could flash the BIOS from there. Guess what? They didn't.

The next thing I'm going to try is to create a bootable DOS CD with my BIOS flash files on it. Hopefully that will work, but I'm sure there'll be some way for that to screw up, too.

The situation is so poor at the moment, that some HOWTOs recommend reinstalling Windows just to flash the BIOS. I mean, seriously, WTF? That's like having to build a clone of Ford's Dearborne plant in your backyard, just so you can replace the wing mirror on your Taurus.

---

### Post by bodhi.zazen on 2008-04-16
Which how-to ?

Try this one :

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

---

### Post by rfruth on 2008-04-16
Some manufactures have a Windows (i.e. EXE) file (only) to aid the flash process, others are gnu / linux friendly - luckily my MSI board offers several formats and I don't need to upgrade anyway :)

---

### Post by Zralou on 2008-04-16
> **kutjara said:**
> 
I tried a bootable USB, because my BIOS says it can boot from a USB stick. Guess what? It can't. The USB drive doesn't light up until Ubuntu is well on the way to being fully booted.


Have you made sure the USB is listed as first drive in BIOS?, and made sure you have a bootable file on the root of the USB?.

Sara Lou

---

### Post by kutjara on 2008-04-16
> **bodhi.zazen said:**
> Which how-to ?

Try this one :

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

Thanks, but that was one of the methods I tried. Unfortunately, the flash files for my machine are bigger than can be accommodated on a floppy, so the procedure failed for me at the "Doublecheck that everything went OK, that those two files weren't too big for the floppy" stage. Even compressed, the zip file was 5MB. 

PC manufacturers no longer feel constrained by what can fit on a floppy when building their BIOS flashes, since the flash process under Windows is done using an executable downloaded to the HDD. As a result, none of the solutions that depend on a floppy (or floppy image) to function will work for large BIOS files.

---

### Post by kutjara on 2008-04-16
> **Zralou said:**
> Have you made sure the USB is listed as first drive in BIOS?, and made sure you have a bootable file on the root of the USB?.

Sara Lou

Oh yes, that was the first thing I did. And I spent many happy hours using various schemes for making my USB drive bootable. None of them work, because the machine simply isn't looking at the USB drive when it boots. Who knows, maybe one of the things the new bios fixes is the problem of not booting from USB. ;)

---

### Post by Zralou on 2008-04-17
Probably not much help to you, but in my BIOS there's a little section that says "allow other drives to boot" (or something along those lines), and that is my USB.  On my BIOS its further down the page than 'select first boot drive', I had to hunt for it first time.

Sara Lou

---

### Post by Robbyx on 2008-04-17
I have just managed to flash the bios. This is how I did it:

I downloaded and burned to a cd  a win98 boot disk iso.
I had trouble with  my floppy drive for the flash upgrade. Therefore I copied the two files on to a usb memory stick that are needed to upgrade the ami bios .

In the bios I disabled the bios protection and changed the boot drive  to the cd drive.
I booted from the cd into dos.

Changed to drive C where my usb stick was recognised. I ran dir from the dos prompt. I ran the bios update program with its bios file from the  C prompt.

Bios updated ok.

I was updating a MSI board P6N SLI

I replaced my cpu with the E8200 and it still does not work even though MSI report it has been tested to work in this board.

I am now back using my old cpu.

Robin

---

### Post by lanzen on 2008-04-21
Thank you all!

I followed the instructions on

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html#comment-1365](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html#comment-1365)

And all was easy and well.   :)

---

