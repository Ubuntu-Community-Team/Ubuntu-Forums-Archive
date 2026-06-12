---
title: "Ubuntu Question"
date: 2007-11-27
forum: General Help
---

### Post by Bigs11 on 2007-11-27
My first HDD is a SATA reserved for WinXP, with a second partition with all my data files on. (My Documents etc...)
I've just installed Ubuntu7 on a second IDE HDD on a Primary Active partition of 20G, with a 5G Swap partition.
I've also installed Fedora8 on the second IDE drive, in the extended partition with the swap partition for Ubuntu.
Grub is installed on root of SATA drive. So when I boot I get Fedora's boot menu, with XP as default, and Ubuntu as the 3rd option.

***My questions are:*** 
I have to reinstall Ubuntu (over the top of it's existing partition), but i'd like to contiue using Fedora's boot menu.
When I install Ubuntu, **can I assign the bootloader to the second HDD root?** (to avoid overwriting Fedora's Grub).
At the moment I can't get Ubuntu to load completely to access it's menu.lst, (which is why I need to reload Ubuntu) and I don't know enough Linux to use the terminal properly.

Is there any to reinstall without reformatting, like you can with XP?

I also would like to use the second Partition of my SATA HDD to save files to from both Ubuntu and Fedora,
but at the moment **in Fedora file manager, it shows a Lock symbol on the My Documents folder** in that drive.
I deliberately made that partition Fat322 so I could read/write from Linux. How can I change this?

In a nutshell, I want to use WinXp as my default OS, using Fedora's boot menu.
And also use the Fat32 partition for saving my data files to from all 3 OS's.

Hope I havn't confused you.
Thanks in advance for any comments.

---

### Post by LaRoza on 2007-11-27
You can install Ubuntu, but do not install grub. Add the contents of Ubuntu's menu.lst (what you want) to Fedora's.

Change the folder "My Documents" to read/write. Right click on it.

---

### Post by viking777 on 2007-11-27
If  you hate terminals as much as I do I suggest you install Krusader file manager, the root mode of which will ease your burden a lot. In answer to your questions though this is what I would do.

Reinstall Ubuntu but when you come to the bootloader installation you have to choose the advanced options (they are well hidden but they are in there) make sure that you get Ubuntu to install the bootloader on its own partition (ie you will have to type (eg.(hd1,2)) do not allow it to be placed on the the root of the drive (ie (hd0,0) Choose whatever is appropriate to your circumstances. 

When the installation is finished you will reboot into the normal Fedora boot menu (Ubuntu will not be listed yet). Your next task is to use Fedora to access your Ubuntu partition and go to /boot/grub/menu.lst and copy the entry for Ubuntu from there and paste it into your Fedora /boot/grub/menu.lst. Next time you boot your entry for Ubuntu will show up as well.

As for your inability to access your shared partition that is probably due to the fact that Fedora sees it as being owned by 'root' not your user name. Unfortunately you are going to have to use a terminal if you haven't got krusder or some other root file manager. I'll assume your shared partition is called 'shared'  it is mounted as 'media/shared', but it really resides at /dev/sda6 and your user name is 'fred' (obviously you need to adjust all of these to suit your circumstances) so:

```
sudo umount /media/shared
sudo chown fred: /media/shared 
mount /dev/sda6 /media/shared
```

Don't forget the colon after your username in command #2 above, and while I am on the subject the commands in the 'code' box above are to be run one line at a time followed by 'enter' they are not to be run all at once.


See how you get on with that.



BTW a 5Gb swap file is ludicrous!! It needs to be about 512Mb max.

---

### Post by Bigs11 on 2007-11-27
Thanks Guys, will try the above. Reason why I chose 5G Swap partition, was I read that you should pick double the size of your Ram. Anyway, will resize it back to about 1G. I've got a 250G drivd and my SATA is 160G, so I'm not too concerned about losing 5G.

---

### Post by viking777 on 2007-11-28
Double the size of your ram was the reasoning when people had about 64Mb of it! Nowadays I read that if you have 2Gb or more of ram then you don't need a swap file at all unless you are heavily into memory intensive items like editing video files. I can't vouch for this, it is only what I have read, but 5GB is very excessive!

Still you obviously don't need the space so it isn't going to do any harm as it is.

---

