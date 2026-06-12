---
title: "How to change DVD burner logical names / drive assignments?"
date: 2007-12-05
forum: General Help
---

### Post by dwasifar on 2007-12-05
I just replaced my IDE DVD burner with a SATA burner.  Now some applications can see it and some can't.  I think it has to do with what logical name they are looking at.  sudo lshw returns this for the new drive:

        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S203B
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/dvd1
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: SB01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=ready
           *-disc
                physical id: 0
                logical name: /dev/cdrom1
 
I think the applications are expecting to see /dev/cdrom and /dev/dvd and not seeing them.  I assume that is because Ubuntu is still holding those logical names for the old drive.  How do I tell Ubuntu to forget about that and assign the default logical names to the new drive?

---

### Post by jfinkels on 2007-12-06
One way to simply solve this problem might be to just use symbolic links.

To link /dev/cdrom to /dev/cdrom1, enter the following in the terminal:```
sudo ln -s /dev/cdrom1 /dev/cdrom
``` Be careful when using the link command! Be sure to read the man page first:```
man ln
``` In the former command, the file following the -s option is the target name, and the last argument to ln is the link name.

---

### Post by dwasifar on 2007-12-06
> **jfinkels said:**
> One way to simply solve this problem might be to just use symbolic links.

To link /dev/cdrom to /dev/cdrom1, enter the following in the terminal:```
sudo ln -s /dev/cdrom1 /dev/cdrom
``` Be careful when using the link command! Be sure to read the man page first:```
man ln
``` In the former command, the file following the -s option is the target name, and the last argument to ln is the link name.

Tried that, it didn't help.  I also tried editing /etc/udev/rules.d/70-persistent-cd.rules.  This caused the logical names to appear correct when you do, say, ls -l /dev/d*, and it fixed a couple more applications, but I still can't get my Wine applications to work,

---

### Post by jfinkels on 2007-12-06
> **dwasifar said:**
> Tried that, it didn't help.  I also tried editing /etc/udev/rules.d/70-persistent-cd.rules.  This caused the logical names to appear correct when you do, say, ls -l /dev/d*, and it fixed a couple more applications, but I still can't get my Wine applications to work,

Are you sure you have the correct mappings in winecfg? IIRC, you need to tell wine to look for letter drives in directories in which a disk has been mounted. I'm not positive on that, though, you will know better than I will.

---

### Post by dwasifar on 2007-12-06
> **jfinkels said:**
> Are you sure you have the correct mappings in winecfg? IIRC, you need to tell wine to look for letter drives in directories in which a disk has been mounted. I'm not positive on that, though, you will know better than I will.
As an experiment, I did a clean Ubuntu install (on a different hard drive) and installed Wine, dvd codecs, and my other applications.  The drive worked correctly under the clean install; but it is slower than the PATA drive it replaced.  I've seen other posts here about flaky support for SATA DVD burners, so right now I'm back to the system's old configuration, and the SATA burner will wait until Hardy.

---

### Post by jfinkels on 2007-12-06
> **dwasifar said:**
> As an experiment, I did a clean Ubuntu install (on a different hard drive) and installed Wine, dvd codecs, and my other applications.  The drive worked correctly under the clean install; but it is slower than the PATA drive it replaced.  I've seen other posts here about flaky support for SATA DVD burners, so right now I'm back to the system's old configuration, and the SATA burner will wait until Hardy.

*shrugs* okey dokey.

---

