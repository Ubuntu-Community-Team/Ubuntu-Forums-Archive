---
title: "Windows partition unavailable after Ubuntu installation on RAID disk"
date: 2015-09-22
forum: General Help
---

### Post by val51 on 2015-09-22
Hi,

First of all, I would like to point out that I am a complete beginner with anything RAID-related, and if there is one good thing to come out of that little experience it is that I will learn a bit more about RAIDs ;)

I inherited a machine from a friend that happens to have two Intel RAID disks - I am not sure which type of RAID exactly, I would be happy to look it up if I know how.

Windows was installed on that machine, and I wanted to install Ubuntu as well. But unfortunately, I was unable to do so using the Ubuntu installer: it was not detecting Windows. After searching around, I entered a few commands using the live disk (I do not remember exactly which ones unfortunately, that was almost a year ago), which finally allowed me to install Ubuntu on the disk.

After this installation, however, Windows was not showing up in the GRUB boot menu. At the time I tried to find how to put Windows back in there, but failed to do so. I left this problem aside for a while, just using Ubuntu.

Now that I have a bit more time, I have been trying to fix this and gain access back to my Windows partition. I have tried mainly using Windows' chkdsk and testdisk on Ubuntu, but with no success.

Here is some information, please let me know what other diagnosis or test I should run to narrow down the problem:

- The Disks tool from Ubuntu shows two NTFS partitions (105 MB bootable, 182 GB), content is listed as unknown.
- The second disk appears as an Intel Matrix RAID Member (version 1.2.00), but I was unable to access any files on this.
- Testdisk sees the partitions as well, but it says the file system seems damaged.

---

### Post by oldfred on 2015-09-22
I do not know RAID, but post this to give more info:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by val51 on 2015-09-22
Thanks for the tip :)


I could not generate a Boot-Info report unfortunately (off to a good start!). However, I think I was able to locate, from my browser history, the one I originally generated almost a year ago when trying to solve the issue in the first place: [http://paste.ubuntu.com/8611910/](http://paste.ubuntu.com/8611910/)


I did not use a live disk since I can access my Ubuntu session fine. I did get the following message when starting Boot-Info:
> [dmraid] packages may interfere with MDraid. Do you want to remove them?
I selected 'No'. if I select Yes, then the next time I run Boot-Info I get
> This will install the [dmraid] packages. Do you want to continue?
and then the message asking me to remove them.


I don't think this is related to the problem I am having though, it seems to get into a GUI issue instead: nothing happens when I click on 'Online report' or 'Local report'. The error output from Boot-Info can be seen here: [http://paste.ubuntu.com/12526418/](http://paste.ubuntu.com/12526418/)


(by the way, I am running Ubuntu 14.04 LTS 64-bit)

---

### Post by oldfred on 2015-09-22
I do not know if you need dmraid or mdmraid.
And Ubuntu version may make a difference. It used to be you only could use the alternative installer for RAID or LVM. But the last alternative installer was 12.04. They then said eventually they would add RAID & LVM to the desktop installer or use server installer & add gui and applications of choice.

Each version of Ubuntu then has gotten closer. LVM is now fully supported with LVM. And latest versions seem to install with RAID, but grub does not install correctly, so RAID is almost supported in gui. But with newest versions.

---

### Post by val51 on 2015-09-22
OK, so I guess I shouldn't have used the desktop installer. But what can I do now to gain access to my NTFS partition, at least just to back up the data I have on there?

---

### Post by oldfred on 2015-09-22
I do not know enough on RAID to know how to mount those partitions. The script was not able to auto mount them, either due to hibernation, needing chkdsk or other corruption. Boot-Repair cannot fix most Windows issues.

May be best to use Windows tools to repair Windows.

---

### Post by val51 on 2015-09-22
OK, I tried chkdsk already (it was recommended by one of the tools I tried on Ubuntu actually) but it was unable to fix anything. I think it could not even recognise the partition.

I don't think I would have attempted an install of Ubuntu with Windows on hibernation mode, but I guess it is worth double-checking. I think I just "broke" some RAID information or something with a command, in my attempt to force the installation of Ubuntu. I did this using the Ubuntu live disk, that's why I'm hoping the solution could be under Ubuntu.

I hope someone with more RAID knowledge can point me towards the right direction :) Thanks for your help oldfred!

---

