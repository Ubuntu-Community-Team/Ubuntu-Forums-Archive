---
title: "Using qemu in Ubuntu"
date: 2005-04-22
forum: General Help
---

### Post by GrumpyBob on 2005-04-22
I am using Ubuntu Hoary.  I've installed qemu 0.6.1-1ubuntu1 via synaptic.  I've broswed aroud the web and found some instructions for how to use it to run Win2k in Debian.

I can create a blank file for qemu to install windows in:
dd of=hd.img bs=1024 seek=2000000 count=0

Then I try to install from a WinNT4.0 CD that I have:
sudo qemu -boot d -cdrom /dev/cdrom -hda hd.img

This seems to set things off quite well, it checks the system, I alter the keyboard and mouse settings, and it formats the virtual hard drive in hd.img.  Then it copies the installation files to hd.img in the WINNT directory.  After doing this, it tells me to remove the CD and restart by pressing enter.  I can remove the CD with some difficulty, but the qemu window complains it can't find the CD-ROM, and siezes up.  If I hit enter without removing the CD, the whole procedure just repeats.

Any ideas what I'm doing wrong?  (If further info needed, I am happy to supply)

I have one or two apps in Windows that I need.  I have Win4Lin 5 but cannot run this with the 2.6.10 kernel, as I've been unsuccessful in patching it. I can run Win4Lin in a  patched 2.6.8 kernel, so running Win via qemu is just a convenience. 

Robert

---

### Post by mpsii on 2005-05-02
After you take out the CD, make sure your line is:
```
sudo qemu -boot c -cdrom /dev/cdrom -hda hd.img
```

Remember, your harddrive is C (-boot c) and your CDROM drive is D (-boot d). If you do not change the line from what you used before, it will attempt to boot with the D drive each time, since that is what you are telling it to do.

---

