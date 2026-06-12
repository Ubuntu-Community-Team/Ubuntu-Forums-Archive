---
title: "The oh-dear-I-accidentally-deleted-Windows-using-rm Post"
date: 2007-06-15
forum: General Help
---

### Post by zheepeez on 2007-06-15
Oh dearie, dearie me...

ok, so I accidentally removed windows. I was removing mount points in preparation for a script that would set up my computer to auto-mount all partitions and I rm'd /media/Windows, completely forgetting that my Windows partition was the one partition that DID auto mount and was thus mounted there.

So I am now, unintentionally, no longer a dual-booter (hooray for me :( )

Anyway, looking at the output of fdisk -l, it seems that the Windows partition was the one with the boot loader on it:

```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1893    15205491    7  HPFS/NTFS
/dev/hda2            1894        5798    31366912+  83  Linux
/dev/hda3            5799        7227    11478442+  83  Linux
/dev/hda4            7228        7296      554242+   5  Extended
/dev/hda5            7228        7296      554211   82  Linux swap / Solaris

```

Does this mean I no longer have GRUB? Or is the boot loader loaded on one of the two 500MB partitions at the bottom? I think I'm going to leave my computer on tonight, and wait until I have an answer

To clarify, /dev/hda1 (the NTFS one) was Windows - now nothing, /dev/hda2 is a seperate ext3 partition I use for media, and /dev/hda3 is my Linux installation. The other two must be swaps or something.

(this is where all those "be careful with sudo!!!" warnings come back to bite me in the proverbial posterior)

---

### Post by musther on 2007-06-15
Did you rm the contents of /media/Winodws, or did you rmdir /media/Windows?

Anyway, if your machine still boots (albeit only into ubuntu) then grub must be contained on some partition which you haven't removed, however it could be loaded from anywhere.

So what happens is this, one of your drives is booted, see which is set to boot from bios, and then use fdisk to find out which partition on that disk is set to boot.  Grub will be set up to load from the MBR of that drive, but then it will call the rest of grub from /boot/grub on one of your partitions, most likely your / (root partition).

I see you only have one drive, /dev/hda.

So grub will be on the mbr of hda (at least, it should be), and rm wont mess with that.  I would think that grub is installed on /dev/hda2 or possibly /dev/hda3, which ever is your root partition, have a look for /boot/grub, if that exists, you should be safe to reboot, but have an ubuntu live CD standing by just in case.

---

### Post by zheepeez on 2007-06-15
thanks.... in response to your first question, the command was ```
sudo rm -r /media/Windows
```...

/boot/grub's there, so I'm assuming it'll go fine - if it doesn't, will I be able to get to my files from the LiveCD? If not, is there a recovery guide somewhere that I can print off in case I'm unable to get to the Internet? 

Cheers

---

### Post by SPr on 2007-06-15
Mis-read OP.

---

### Post by stchman on 2007-06-15
> **zheepeez said:**
> Oh dearie, dearie me...

ok, so I accidentally removed windows. I was removing mount points in preparation for a script that would set up my computer to auto-mount all partitions and I rm'd /media/Windows, completely forgetting that my Windows partition was the one partition that DID auto mount and was thus mounted there.

So I am now, unintentionally, no longer a dual-booter (hooray for me :( )

Anyway, looking at the output of fdisk -l, it seems that the Windows partition was the one with the boot loader on it:

```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1893    15205491    7  HPFS/NTFS
/dev/hda2            1894        5798    31366912+  83  Linux
/dev/hda3            5799        7227    11478442+  83  Linux
/dev/hda4            7228        7296      554242+   5  Extended
/dev/hda5            7228        7296      554211   82  Linux swap / Solaris

```

Does this mean I no longer have GRUB? Or is the boot loader loaded on one of the two 500MB partitions at the bottom? I think I'm going to leave my computer on tonight, and wait until I have an answer

To clarify, /dev/hda1 (the NTFS one) was Windows - now nothing, /dev/hda2 is a seperate ext3 partition I use for media, and /dev/hda3 is my Linux installation. The other two must be swaps or something.

(this is where all those "be careful with sudo!!!" warnings come back to bite me in the proverbial posterior)

Did you have ntfs-3g installed and have your fstab with ntfs-3g in the line that mounts Windows?  If not then Windows is still there.

---

### Post by musther on 2007-06-15
It's possible that you just removed the mount point, and not all of the files, but the only way to find out is to try.  Yes, you can get to your files from the live CD, you should be able to get online too.

---

### Post by Old *ix Geek on 2007-06-15
I'm sorry--I know this is a serious issue for you, and I'm not trying to make light of that--but as soon as I read what you'd done, I thought about this design in my shop:

[[IMG]http://www.smartassproducts.com/images/rm_windows.jpg[/IMG]](http://www.cafepress.com/saproducts/790448)

---

### Post by szaka on 2007-06-15
> **Old *ix Geek said:**
> I'm sorry--I know this is a serious issue for you, and I'm not trying to make light of that--but as soon as I read what you'd done, I thought about this design in my shop:

[[IMG]http://www.smartassproducts.com/images/rm_windows.jpg[/IMG]](http://www.cafepress.com/saproducts/790448)
We have done this thousands times with dozens of real-world Windows images. It's part of the NTFS-3G quality assurance process: [http://ntfs-3g.org/quality.html#testmethods](http://ntfs-3g.org/quality.html#testmethods) Typically it takes a few minutes. Could we use the image in the future? ;-)

@zheepeez: You should be able to restore all your files with a good recovery software. Technically this is possible. NTFS-3G doesn't delete the file contents, it only marks files as being unused so the undelete operations can succeed. Provided you didn't write to the partition since then.

---

### Post by strabes on 2007-06-15
If you still need to install GRUB check this page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Old *ix Geek on 2007-06-16
> **szaka said:**
> We have done this thousands times with dozens of real-world Windows images. It's part of the NTFS-3G quality assurance process: [http://ntfs-3g.org/quality.html#testmethods](http://ntfs-3g.org/quality.html#testmethods) Typically it takes a few minutes. Could we use the image in the future? ;-)
Anything's possible!  Please e-mail or PM me and we'll discuss it.

---

### Post by zheepeez on 2007-06-17
Yes, it was mounted, and yes, I did have ntfs-3g running, so it's well gone.. I haven't written to the partition since then, so it's possible to get it back? What kind of ntfs restore software is there?

---

### Post by musther on 2007-06-17
There's a whole heap of software for windows, some free, some free trial.  So if you can put it in another machine, then that's an option - just google it.  If you need to do it from within Ubuntu, I have no idea (but I'll look), but maybe somebody else can help.

---

### Post by szaka on 2007-06-18
> **zheepeez said:**
> Yes, it was mounted, and yes, I did have ntfs-3g running, so it's well gone.. I haven't written to the partition since then, so it's possible to get it back? What kind of ntfs restore software is there?
ntfsundelete on Linux from the ntfsprogs package.

---

