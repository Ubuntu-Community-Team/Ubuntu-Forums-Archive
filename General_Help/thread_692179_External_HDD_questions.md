---
title: "External HDD questions"
date: 2008-02-09
forum: General Help
---

### Post by FlamingGooch on 2008-02-09
Hey everyone. I have a quick question and was wondering if this is plausible and/or has been done before (which I imagine it has).

What I want to do is dual boot Windows XP and Ubuntu on my laptop's internal hard drive and use the external hard drive (500 GB) to store everything that Linux and Windows will use. For example, I'll have all of my computer games on the external drive and just run Windows from my internal hard drive. Same thing for Ubuntu; I'll have the OS on the internal drive and everything that it uses and everything that I download or install on the external drive.

Can this be done or should I just install Ubuntu to the external drive? I have my doubts about installing directly to the external drive because what I've read so far says that to make it right the first time you have to unplug your internal hard drive completely and this is not an option for me.

Thanks.

---

### Post by ajgreeny on 2008-02-09
You can install ubuntu to the external drive without detaching the internal hard drive, but it will be easier to use the alternate install CD.  When using this, just install ubuntu to the external hard disk using the text based installer as usual, but when you get to the grub installation, make sure you put grub on the external drive, not the internal one.  Now set your BIOS to boot first from the external drive and second from the internal drive.

Now when you boot up with the external drive attached, grub will appear and you can chose either windows or ubuntu, but if the external drive is not attached, grub will be bypassed and the windows MBR will start as usual and windows should boot as it does now.

As to whether it is wise to put all your games and installed programs on the external drive, depending on what you mean by that it may or may not be possible.  Data files can certainly go on it, ie. everything currently in the My Documents folder in windows, but I fear you could possibly run into problems if you put the stuff normally in Program Files or in the linux usr/bin folders onto the external drive.  I could be wrong and if so I'm certain someone else will tell both of us, but I think it safer to just use the external drive for data files and not any programs.

---

### Post by FlamingGooch on 2008-02-10
> **ajgreeny said:**
> As to whether it is wise to put all your games and installed programs on the external drive, depending on what you mean by that it may or may not be possible.  Data files can certainly go on it, ie. everything currently in the My Documents folder in windows, but I fear you could possibly run into problems if you put the stuff normally in Program Files or in the linux usr/bin folders onto the external drive.  I could be wrong and if so I'm certain someone else will tell both of us, but I think it safer to just use the external drive for data files and not any programs.

Is it possible that I could give the linux ext3 file system partition a certain size and format the rest of the drive to be an NTFS partition?

---

### Post by FlamingGooch on 2008-02-11
bump

---

### Post by ajgreeny on 2008-02-11
I think that you could do that, now that ubuntu has read/write permission to ntfs partitions.  Make sure you have the ntfs-3g and ntfs-config installed and then make sure the partition is mounted at boot time by using the **System Tools>NTFS Configuration Tool** in the menus.  I'm not sure about putting your /home folder on NTFS, though so think that would be best on an ext3 partition as is the default for ubuntu, but your data files eg docs, photos, music and videos can go on the ntfs partition as far as I'm aware.

---

