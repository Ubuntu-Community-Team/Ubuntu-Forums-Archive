---
title: "install ubuntu on whole hard drive"
date: 2014-05-15
forum: General Help
---

### Post by williambiggs31 on 2014-05-15
I need to install ubuntu on my mom computer . She dose not have a blank dvd or usb she has windows 7 on it but we need to replace the whole disk with ubuntu and remove windows . How can I do it with out a dvd

---

### Post by dragonfly41 on 2014-05-15
That is a problem .. it would make your task much easier if you could purchase or borrow some blank dvds or a usb flash drive.

But if this is not an option then one approach might be to first setup a *dual boot* configuration.   Read up on dual boot in this forum.

When ubuntu is working .. and only then .. you can delete windows 7.   I would keep your computer running until all these steps are completed.

...

In windows 7 shrink the disk partition to allow a logical (extended) partition to be created towards the end (right) of the drive (windows 7 must remain in the first partition to work). This logical partition will contain the ubuntu partition(s).

[http://technet.microsoft.com/en-us/magazine/gg309170.aspx](http://technet.microsoft.com/en-us/magazine/gg309170.aspx)

In the logical partition the created partitions are to be ext4 (not FAT or NTFS) for Ubuntu installation.

[http://superuser.com/questions/424907/how-do-i-format-a-drive-as-ext4-on-windows-7](http://superuser.com/questions/424907/how-do-i-format-a-drive-as-ext4-on-windows-7)

Download and install partition wizard (free home edition).

[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

Note that there are options for ext2, 3 or 4 formats.  Choose ext4 .. for ubuntu .. but you might add another partition to hold important windows data before deleting windows

[http://www.partitionwizard.com/help/create-partition.html](http://www.partitionwizard.com/help/create-partition.html)

You could then have this disk structure ..

c: windows 7
d: recovery
e: logical partition
      f: ext4 partition for /   (ubuntu root)
      g: ext4 partition for /home (ubuntu home)
      h: Linux swap for /swap (ubuntu swap)
      i: NTFS partition for backing up data from windows 7 (windows bookmarks, email databases?).   

I can guarantee that after deleting windows you will wish that you had backed up some data you overlooked in this migration.

Now install unetbootin to run in windows 7.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe](http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe)

Now download the ubuntu *.iso of your choice to save in windows 7 download folder.

Now launch unetbootin and search for the source ubuntu *.iso by selecting
Diskimage ISO .. browse to the ubuntu *.iso.

Set ..

Type: Hard disk
Drive: .. look for the ext4 partition you have created

Be very careful to select the target partitions for installation of ubuntu since if you select (by error) the windows c: partition you could end up overwriting windows (you need to keep windows running throughout this).

Allow unetbootin (running in windows) to install ubuntu as above into ext4 partition.

...

[COLOR=#b22222]Caveats: [/COLOR]

It has been some time since I've used unetbootin in windows so I'm rusty on this .. do your research first.   Wait for other suggestions in this thread (I might have missed a step such as setting up grub in dual booting).

Make sure that your windows data is backed up.   Consider buying some blank dvds or a low cost USB flash drive. 
It would make this migration much easier.

While windows is still running consider opening dropbox and spideroak free accounts for backup of windows data.

---

### Post by mörgæs on 2014-05-15
Would be easier just to test Buntu in a live boot.

---

### Post by dragonfly41 on 2014-05-16
> Would be easier just to test Buntu in a live boot.

mörgæs .. the OP did explain the constraint that there are no blank dvd's or usb flash drive for burning live boot ubuntu. So .. no external media for live booting.  This is why this proposed migration process is so convoluted. 

This thread .. [http://askubuntu.com/questions/254407/can-i-install-ubuntu-from-an-iso-file-on-windows](http://askubuntu.com/questions/254407/can-i-install-ubuntu-from-an-iso-file-on-windows) ..

suggests that wubi.exe can be added to the downloaded *.iso 

so this might be another option to try.

There are the options of installing ubuntu either by wubi (integrating with windows) or installing VirtualBox in windows and then installing ubuntu as vm in windows.

But these do not meet the OP's requirement to completely wipe windows after ubuntu is installed (and then the freed disk space would need further attention to tidy up).

EasyBCD is another windows option to try instead of unetbootin.   But there must be some partitions created by windows (ext4 format) to receive the target ubuntu installation.

I hope I'm not missing a trick here.   But there are no external media options.

I still think it would be much easier to buy/borrow a usb flash drive.  It will be needed at some later stage.

---

### Post by LastDino on 2014-05-16
Well, if you do own some MicroSD card of 4GB and card reader (both are super cheap and lt's likely that you already have them, or at least one of the two), you can use it as USB and follow the very same Live USB thing to both test and install Ubuntu on your grandmothers PC. I've tasted this multiple times and it has never failed me, it does take little longer for whole procedure though, but that to depends on the class of that card and worthiness of that card reader.

---

### Post by Impavidus on 2014-05-16
Getting a cheap (&#8364;7 at my local computer hardware shop) usb drive for a live boot would be the easiest option by far, but there is a way via wubi.

1. Use the Windows partioning tool to create empty space at the end of the disk, where a ca. 25GB extended partition can be created.
2. Install Ubuntu via Wubi and boot Ubuntu.
3. Install gparted and create an extended partition at the end of the disk. In the extended partition, create an ext4 partition for root and a swap partition.
4. [Migrate Wubi]("https://help.ubuntu.com/community/MigrateWubi") to the ext4 partition, with swap and with grub bootloader.
5. Reboot to start the Ubuntu installed on its own partition.
6. Use gparted to delete the Windows partition(s) and replace it with an ext4 partition. This will be the /home partition.
7. Update grub to remove Windows from the grub menu.
8. [Migrate the home directory]("https://help.ubuntu.com/community/Partitioning/Home/Moving") to the new /home partition.

I never tried this myself, nor have I ever heard of someone trying this, but I think it should work. Note that it is best to have a live disk at hand, because it can be a great tool to rescue your system if something goes wrong.

---

### Post by mörgæs on 2014-05-16
When given the choice a) proceed through the steps outlined above or b) buy a blank DVD I guess most beginners would pay a few coins for the convenience and security. The same goes for experienced people. 

If Lubuntu 14.04 is considered a DVD is not even necessary. A CD will do.

William, now you know the options. What do you prefer?

---

