---
title: "[SOLVED] DVD burner is not reconised correty"
date: 2007-04-23
forum: General Help
---

### Post by uclalinux on 2007-04-23
I have a DVD burner on the front is says DVD+RW, i bought DVD+R, i have written to these dvd's before using these DVD+R dvd's, and the same DVD burner. I had to reinstall ubuntu, and now I can't burn to these dvd's.  K3B says i have a DVD-RW and wont let me burn to them,  It  says to put in a DVD-R.  Even thought on the front of my dvd burner it says DVD+RW

I know it must be a simple solution, because i was used ubuntu before to burn these same dvd's and dvd burner.

Here is my fstab if it is any help. 
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=28004ca4-3f61-4b1f-b0df-f317cecb3792 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=98aff16d-ce57-4a32-87c5-597bc759fc00 none            swap    sw              0       0
/dev/hdc        /media/dvd   auto  noauto,ro     0       0

#  /dev/hdb1
UUID=ab344534-5232-49f6-a800-341da5b03b26  /home/hdb1  ext3 defaults 0 2

---

### Post by mdurham on 2007-04-23
> /dev/hdc /media/dvd auto noauto,ro 0 0
do you actually have a /dev/hdc? I had the same line in my fstab from a fresh install but don't have a /dev/hdc.

---

### Post by uclalinux on 2007-04-24
the hdc is my dvd burner

---

### Post by mdurham on 2007-04-24
> **uclalinux said:**
> the hdc is my dvd burner

Do you actually **have a file** "/dev/hdc"?   I don't have one.

---

### Post by uclalinux on 2007-04-30
huh? it is under a device. my dvd burner is on the IDE cable 2nd Master, it is label as /dev/hdc

---

