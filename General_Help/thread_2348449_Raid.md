---
title: "Raid"
date: 2017-01-03
forum: General Help
---

### Post by kcmccombs on 2017-01-03
hello I have a question? if i have a raid setup in one debian base and i want switch to a different distro will i be able to keep the raid or will i lose it.thanks

---

### Post by Olav on 2017-01-04
1. Backup your files, whether they are on RAID or not. [RAID is not a backup solution](https://duckduckgo.com/?q=RAID+is+not+a+backup+solution).
2. If you have not made a backup yet, refer to point 1.
3. You should be able to keep your existing array during installation, but tread carefully. It depends on the way you created the array and the installation program of your new distribution. You may have to select something like "advanced" and/or "expert" installation mode at the start of installation and certainly you need to choose manual disk selection/partitioning. If your new OS is a recent Ubuntu (or derivative), use the [Netboot installer](http://cdimage.ubuntu.com/netboot/xenial/) (mini.iso). It will recognise the array but you must not make any mistakes during these steps:

Choose **Manual** and hit Enter:

[ATTACH=CONFIG]273031[/ATTACH]

Your array will be there, select it and hit Enter:

[ATTACH=CONFIG]273030[/ATTACH]

Select **Use as** and choose the proper file system for the array (i.e. the one it was already formatted as), then make sure that after **Format the partition** it says **no, keep existing data**. Then name the mount point (could just be / or whatever):

[ATTACH=CONFIG]273032[/ATTACH]

Configure the rest of your partitions as needed.

If you have not used the Netboot installation program before, you may want to practice with it a few times on another computer or virtual machine. Don't just boot it up on the computer with the important files if you are at all unsure. Luckily, if you have used the Debian installer before you will feel quite at home (but some steps are slightly different/in a different order).

Good luck. Without any knowledge of your system I think it is almost impossible to give you further advice.

---

### Post by kcmccombs on 2017-01-04
okay thanks for the reply and help. i guess i left out a few thing my existing OS is on a ssd all to it self if i install the new OS back to the same ssd will it see the other drives as a raid set.i do not use this as a backup.thanks

---

### Post by Olav on 2017-01-04
> **kcmccombs said:**
> okay thanks for the reply and help. i guess i left out a few thing my existing OS is on a ssd all to it self
The SSD makes no difference. But wait a second. We are speaking of software RAID, is that correct? This was what I was assuming earlier. Should have asked. Or do you have a hardware SATA/RAID controller in your computer and did you configure the array in some sort of BIOS-like setup environment? That would change quite a few things.

It could possibly make your life a lot easier. If you just boot a Ubuntu Live DVD/USB and the file system on your RAID is recognised, there would be no need for any special setup procedures. You can try this out without any special risk, and without committing to an install.

> **kcmccombs said:**
> if i install the new OS back to the same ssd will it see the other drives as a raid set.
Back assuming software RAID: The graphical installation program that comes with the Ubuntu Desktop ISO will not see it. It will only see the members of your array as separate disks or partitions, each with an "unknown" file system. The installer from the Ubuntu Netboot (and I guess, the Server) edition will correctly recognise your RAID members and the array itself, the way I showed you previously.

Of course you can still use a Desktop ISO to install and leave your "unknown" drives not configured. In that case be careful not to let the installer do anything to them. Unplug them just to be sure. Then after installation, recreate the array (or RAID set if you will) manually from the member drives and add the array as a filesystem to your /etc/fstab. You can search for the mdadm command line program which manages RAID configurations, there is a lot of information out there. I would also have to search for the exact commands, it is not something I do every day.

> **kcmccombs said:**
> i do not use this as a backup.thanks
I am not sure we are understanding each other correctly. Presumably, since you are running some kind of RAID (I suppose RAID1 or RAID5, right?), the files that you keep on there have some value for you. That is exactly why you need to back them up, regularly, **in addition to** keeping them on RAID. RAID does not protect against most accidents that may happen to your files. At all. Especially not if you start messing with your system...

Been there, done that, had to restore from tape.

---

### Post by kcmccombs on 2017-01-04
ok thanks for the quick replies i should have started off with my  complete setup. i have 1 ssd with my OS, 6 3tb (raid 10) with  (mdadm  software raid) it took about a day trying not to go through that again   all the raid is used for  my plex media and 1 ext usb hdd for DLs. the  only thing i am trying to achieve is basically just to change my OS th  Ubuntu desktop i have only been using Linux for about a month so not  very familiar with everything yet. i apologize for not being more  descriptive in the beginning. thanks for the help

---

### Post by SeijiSensei on 2017-01-05
If the device uses mdadm for software RAID, it should be visible to any Linux distro. To be sure, use the installer disk to run a live session (rather than installing) then see if you can mount the array.

---

### Post by kcmccombs on 2017-01-05
okay thanks will give it a try

---

### Post by kcmccombs on 2017-01-06
thanks for all the help found some good directions on using mdadm thanks again

---

