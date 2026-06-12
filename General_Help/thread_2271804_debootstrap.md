---
title: "debootstrap"
date: 2015-04-01
forum: General Help
---

### Post by HowIsThisWorking on 2015-04-01
Hello,

I am trying to install ubuntu on a laptop that i found in my attic. The computer has a serial floppy drive (add-on) and a usb 1 slot. I can only boot from the hard drive or the floppy disk. I was able to get most of the was there (I think) because of this tutorial with a few tweaks. This is what I have done so far (I will only list changes that I had to make for my machine):

[https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)

I had to download the image files from here (Boot, Root, and net_drivers):
[http://archive.debian.org/debian/dists/sarge/main/installer-i386/current/images/floppy/](http://archive.debian.org/debian/dists/sarge/main/installer-i386/current/images/floppy/)

**Started the computer with the Boot floppy:**
expert acpi=off

**Mirror Settings**
snapshot.debian.org
/archive/debian/20070101T000000Z

Instead of installing debian at this point, I pressed ALT+F2 to open another console as suggested by the guide.

**Getting debootstrap** (The link that was provided no longer works so i went to the archive link.)
wget [http://archive.ubuntu.com/ubuntu/pool/main/d/debootstrap/debootstrap_1.0.67_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/debootstrap/debootstrap_1.0.67_all.deb)

Followed the steps after, but when I ran:

/usr/sbin/debootstrap --variant=minbase --arch i386 precise /target [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

I get an error stating:

I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
**E: Cannot check sha1sum**

This is where im stuck. The error seems to be in the debootstrap program.
**/usr/share/debootstrap/functions** verify_checksum ()

I know this is not a normal situation considering all of the steps this process requires but any help would be appreciated!

Thank You

---

### Post by bardo2 on 2015-04-03
As you are able to connect to a network, you wont need to go thru debootstrap (i wouldnt, its complicated). Once you get just the few disk sectors needed to get to grub (maybe dd from a file), you could setup a boot entry to boot from the ubuntu ISO. For me, this has always been a handy recovery option. Just be aware, that you will not be able to install ubuntu onto the partition, where the ISO is stored.

---

