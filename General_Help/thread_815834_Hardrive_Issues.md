---
title: "Hardrive Issues"
date: 2008-06-02
forum: General Help
---

### Post by CelticShamrock on 2008-06-02
I recently switched from Windows Vista to Ubuntu. When I made the switch I did the trial version first, the one where it says install on the Ubuntu desktop while checking it out. While I was in this trial version I had access to all of my old files from windows. I installed Ubuntu completely and am running it as I type, my problem however is that my harddrive is not accessible at all. I can not find it anywhere, I searched google and Ubuntu but to no avail. PLEASE help me.

---

### Post by Rocket2DMn on 2008-06-02
Did you just overwrite your windows installation where all your files are stored?  If so, then your files are gone.  Can you please post the output of
```
sudo fdisk -l
mount
```

---

### Post by jualin on 2008-06-02
Did you install Ubuntu using the Wubi Installer (installer within windows)?. Because if you did the  windows files should be under "/host". Hope this helps

---

### Post by CelticShamrock on 2008-06-02
I did not install in windows, and where would I type that command in? There doesn't seem to be a command prompt.

---

### Post by CelticShamrock on 2008-06-02
I don't mind about files, but I need the hardrive space. It isn't showing up as an available drive under Places/My Computer.

---

### Post by jualin on 2008-06-02
Are you able to log in into Ubuntu?. If you are you have to go to Accesories and then Terminal to type what Rocked2D suggested. Can you boot up windows?, If you can try doing a clean shutdown from windows, this is a common solution many times. Post your results.

---

### Post by CelticShamrock on 2008-06-02
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14074   113049373+  83  Linux
/dev/sda2           14075       14593     4168867+   5  Extended
/dev/sda5           14075       14593     4168836   82  Linux swap / Solaris



And I can not boot windows. I have the disc but no space to save it to.

---

### Post by Rocket2DMn on 2008-06-02
It appears that you completely overwrote windows, there is no ntfs partition there.  This means that all your files are gone.  Sorry to disappoint.  This is another example of why everybody should always keep complete and up to date backups (on external HDs, or flash disks, or CDs/DVDs).

---

### Post by jualin on 2008-06-02
And finally if this doesnt work you may want to open up Synaptic Package Manager from System, Administration and  install "ntfs-3g" and "ntfs-config". And then try to enable your partition manually.

---

### Post by jualin on 2008-06-02
according to your results, you wiped out your windows partition,  am i right Rocket?

---

### Post by CelticShamrock on 2008-06-02
Does that mean that I can not get that disc space/hardrive back?

---

### Post by jualin on 2008-06-02
You can get the space back but your Windows is completely erased, therefore your windows files are not available.

---

### Post by CelticShamrock on 2008-06-02
How do I get the space back, then I can re-install windows. All I had really was some porn and music.

---

### Post by Rocket2DMn on 2008-06-02
This means your files are gone gone as in not coming back.  What do you want to do now?  Completely remove Ubuntu and return to windows?  Setup a dual boot with Ubuntu and windows?  Just keep Ubuntu and start fresh?

---

### Post by CelticShamrock on 2008-06-02
I was hoping to have a dual boot at the beginning of this, so that.

---

### Post by jualin on 2008-06-02
install windows and during the windows installation specify 2 partitions one for windows and the rest for Ubuntu. The Install ubuntu and make sure you use the Blank partition.

---

### Post by CelticShamrock on 2008-06-02
But when I go to install windows I can not see my hardrive. It is missing.

---

### Post by cybrsaylr on 2008-06-02
> **CelticShamrock said:**
> Does that mean that I can not get that disc space/hardrive back?

It looks like you wiped out Windows.
I also have a 120GB HDD.
Here's how my dual boot setup looks:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x018d8dfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433       14593    97683232+   f  W95 Ext'd (LBA)
/dev/sda5            4865        9695    38804976    7  HPFS/NTFS
/dev/sda6            9696       14593    39343153+   7  HPFS/NTFS
/dev/sda7            2433        2493      489919+  82  Linux swap / Solaris
/dev/sda8            2494        4864    19045026   83  Linux

To get your space back for Windows you have to format your HDD again and reinstall Windows and start over. Setting up a dual boot setup is tricky. I messed my PC up 3 times before getting it right. Now it runs great.

---

### Post by jualin on 2008-06-02
Are you trying to install Vista or XP? If you install XP you should be able to delete the partition during the installation. I think that it says something like "Unrecognized Space" or something similar, but you can delete it and then create a new partition right away. You should specify the size so it can be like half of your Hard drive space.

---

### Post by CelticShamrock on 2008-06-02
I have Vista. I'm going to try and see if the windows install disc works. Be back in a few.

---

### Post by Rocket2DMn on 2008-06-02
You should have a look here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
You will need to resize your Ubuntu partition first to make room for windows.  This can be done using GParted on the Ubuntu LiveCD (System->Adminstration->Partition Editor) or using the [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/")
You can then install windows to the newly freed space.  After that you will have to reinstall GRUB because windows will overwrite the MBR - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Alternatively, you can just reinstall windows fresh over the entire hard drive, thus eliminating your current Ubuntu install.  Then pull out the Ubuntu install cd and setup for a dual boot by shrinking the windows partition from within the installer.  This is the suggested order of installation so that you don't have to reinstall GRUB.

---

### Post by CelticShamrock on 2008-06-02
When I try and re-install windows it says the hardrive isn't NTCSF supported (or some combination of those letters) and that I can not save it.

---

### Post by Rocket2DMn on 2008-06-02
That would be NTFS.  If you are going to just wipe the drive clean and do the install windows first followed by installing Ubuntu, you must DELETE the existing partitions before you can install to the drive (so that you install to unallocated space).

---

