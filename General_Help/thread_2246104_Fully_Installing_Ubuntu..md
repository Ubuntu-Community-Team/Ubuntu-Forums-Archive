---
title: "Fully Installing Ubuntu."
date: 2014-09-28
forum: General Help
---

### Post by rapzeh on 2014-09-28
I've installed Ubuntu on my 2nd Hard Drive, and I very soon plan on switching over fully now that CS:GO is on Linux, BUT, how do I erase the Hard Drive Windows is on following the transition, and more importantly, provided I ever do need to re-install Windows, how would I go about doing it?

Cheers!

---

### Post by whitesmith on 2014-09-28
I've read this post twice and I'm not sure I understand it. Are you saying you have two HDDs in a box, one with Ubuntu and one with Windows, and you sometime in the future want to erase the second one? If that is the case just use gparted to remove the partition.

---

### Post by rapzeh on 2014-09-28
Right. I have two hard drives in one box. One has Ubuntu, and one has Windows. I want to erase the one with Windows on it and be able to use it with Ubuntu.

BUT, I also want to know, how will this effect me if I want to re-install Windows in the future for whatever reason.

---

### Post by blackbird34 on 2014-09-28
Why not just shrink the windows partition down to ~100GB (with the Windows partition tool, NOT GPARTED)? Then you'll have some extra space _and_ avoid having to go through all the hassle of installing Windows...

---

### Post by buzzingrobot on 2014-09-28
If the Windows disk has a Windows recovery partition on it, and you remove the Windows partitions on that disk, repartition it and install Ubuntu, then the Windows recovery partition will, of course, be gone. Reinstalling Windows, then, would require either a Windows installation DVD or a set of Windows recovery disks you may have made. (if you have not made a set of recovery disks, and your Windows installation offers that as an option, I'd recommend doing it, even if you have a full Windows install DVD handy  The recovery disks -- you'll need several -- return the system to its factory default, including drivers.)

---

### Post by nerdtron on 2014-09-28
> Right. I have two hard drives in one box. One has Ubuntu, and one has  Windows. I want to erase the one with Windows on it and be able to use  it with Ubuntu.

BUT, I also want to know, how will this effect me if I want to re-install Windows in the future for whatever reason. 

First things first, since this is a 2 hard drive install, it would be easier to use the windows drive if we are sure that grub is installed on the second hard drive where Ubuntu is installed.

Remove the 1st hard drive (with windows) and boot your computer only using the second hard drive. If Ubuntu boots successfully we can continue. If not, we need to fix this first.

---

### Post by ian-weisser on 2014-09-29
> **rapzeh said:**
> how do I erase the Hard Drive Windows is on following the transition, and more importantly, provided I ever do need to re-install Windows, how would I go about doing it?

If you had a single hard drive:

1) Create a Windows Recovery USB stick (or other media), if Windows offers this option. Label it, so you don't overwrite it with something trivial in a few months.
To reinstall windows, boot from this recovery media.

2) Backup all the data you want to save to external media. Everything on your hard drive is about to be erased.
Label this backup. If you reinstall Windows, your data is not included.
Import the data to Ubuntu after installation.

3) Boot the Ubuntu installer.
Select 'Try Ubuntu'.
Make sure your hardware works with Ubuntu. Then select 'Install'. 
Select the default settings - it will repartition the drive and overwrite Windows.

4) Finally, import your data into Ubuntu.
After Ubuntu is installed and rebooted, insert the external media with your data backup.
Copy your data into your new Ubuntu environment.

If you wish to destroy Ubuntu and restore Windows, then the process is similar:
- Backup all your data to an external drive before it's erased.
- Boot from the Windows Restore Media. It will overwrite Ubuntu.
- Import your data from the external drive after Windows is up and running.


But you have TWO hard drives. That makes things easier.
If you think you may want to restore Windows, then simply don't erase that hard drive yet.
Hard drives are pretty cheap. Unplug it instead. Nerdtron is right; change the disk you boot from instead.

Do backup you data. And do import your data into Ubuntu.
If you're not up to cleverly mounting and reading the Windows disk from Ubuntu, then use a USB stick.

Someday, when you are sure you're ready to erase Windows from that hard drive, it's very easy.

---

