---
title: "Creating space for partition on HDD"
date: 2016-08-30
forum: General Help
---

### Post by lloyd-connellan on 2016-08-30
Hello all. I've been wanting to install Windows 7 dual boot alongside Ubuntu (already installed) and have been having some problems creating space for the partition (yes ideally it would be better to install Windows first and then Ubuntu, but unfortunately that's not really an option). To explain my setup, I have a 120GB SSD with Ubuntu 16.04 installed and a 1TB HDD for storage with 300GB of files already on it I'd rather not delete. What I would like to is put Windows on the HDD since I don't really have enough space on the SSD for both operating systems, but I've not been able to do this. Here are the things I tried so far:


**gparted**


Firstly I tried shrinking the space on the HDD with gparted. This was done after unmounting the drive while logged into Ubuntu (I also tried this from a live USB but it made no difference). The problem I found which is shown in this screenshot: [http://imgur.com/a/yL2h8](http://imgur.com/a/yL2h8), is that it cannot "read the contents of the filesystem". The filesystem seems to be in an NTFS format typically used for Windows (why it is using this format when Windows hasn't ever been installed on this computer, I don't know). The error suggests installing ntfs-3g, but it is already installed (ntfs-3g in terminal clearly works). Any attempt to resize the partition fails since it can apparently only make room for 2MB. 


**ntfsresize**


Next I tried using ntfsresize on the command line to resize it. Specifically I tried this command:


```
sudo ntfsresize -s700000M /dev/sdb1

```


Here the idea was to shrink the partition to 700GB, leaving 300GB left for Windows. But it failed and gave me this error:
> 
ERROR: Filesystem check failed!
ERROR: 278804 clusters are referenced multiple times.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.


So clearly it finds something wrong with the filesystem and wants me to repair it in Windows... but of course Windows isn't installed in the first place so I can't do that. Google suggested maybe something like this might work:
```
sudo ntfsfix /dev/sdb1
```


and it seems promising at first:


> Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sdb1 was processed successfully.


but alas I still get the same error if I run ntfsfix again.


**Windows?**


Finally I thought maybe after all Windows could solve the problem for me with that chkdsk command. Booting up with a USB with Windows 7 on it, it seemed there was no way for me to install it on the HDD without a free partition, although I found out you can run the cmd line using SHIFT-F10. So I tried the command mentioned earlier: chkdisk /f. That didn't work since the drive is 'write-protected' but I was able to do get it working using chkdisk C: /f /r /x. This appeared to be doing something, and it seems it randomly ended up deleting two files with colons in their names. When I went back into Linux though it was still giving me the same problems.

So now we are here. I don't suppose anyone knows what could be causing this? Ideally I'd rather not ask, but I haven't seen this error anywhere else. Any help would be appreciated.

---

### Post by TheFu on 2016-08-30
Back everything up, then reformat however you like.  Backups aren't just for protecting data, but for solving issues like this without nearly so many hoops.  Plus they are great when a HDD fails and we actually have backups in advance.

Why would a disk come preformated with NTFS? Because most of the world uses NTFS and vendors have learned it is easiest to make life easy for the masses and avoid returns this way.

Always look at the file system before using it. Always.

---

### Post by lloyd-connellan on 2016-08-30
That is probably the most sensible option. I was kind of hoping I could be cheap and not buy another HDD just for backing up data, but it certainly wouldn't be a bad idea. 

As for choosing the right file system in the first place, yeah I guess that's hindsight. It was many years ago and I honestly didn't give it a second thought at the time.

---

### Post by TheFu on 2016-08-30
Whenever changing partitions (resizing, adding/deleting), there is a chance of complete data loss. Backups are needed to limit that risk.

While you are at it, consider whether MBR or GPT would be best/required in the setup. For a linux-only solution, I'd use GPT 100% for the better flexibility, larger sizes, better redundancy, etc., but Windows has some limitation on GPT use of boot devices that would be smart to know in advance.

Another option that doesn't involve repartitioning is to use virtualization. Is that an option for your needs?

---

### Post by grahammechanical on 2016-08-30
Does not the Windows install disc have a partitioner that will shrink that partition to create unallocated space for new Windows partitions? See section 8 drive options>Advanced>Extend.

[http://www.sevenforums.com/tutorials/1649-clean-install-windows-7-a.html](http://www.sevenforums.com/tutorials/1649-clean-install-windows-7-a.html)

> To **shrink an existing partition** to create another partition to install Windows 7 on instead, select the partition you want shrink and click on the **Extend** option. Type in how much in **MB** (1 GB = 1024 MB) that you want to shrink it by. Now select the new extended partition.

Regards

---

### Post by lloyd-connellan on 2016-08-31
> **TheFu said:**
> Whenever changing partitions (resizing, adding/deleting), there is a chance of complete data loss. Backups are needed to limit that risk.

While you are at it, consider whether MBR or GPT would be best/required in the setup. For a linux-only solution, I'd use GPT 100% for the better flexibility, larger sizes, better redundancy, etc., but Windows has some limitation on GPT use of boot devices that would be smart to know in advance.

Another option that doesn't involve repartitioning is to use virtualization. Is that an option for your needs?

The only real reason I need the windows partition is to play games, and I believe a virtual box isn't really good for that. So I will probably just go for reformatting my HDD once I have a backup. Anyway thanks for the advice.

> **grahammechanical said:**
> Does not the Windows install disc have a partitioner that will shrink that partition to create unallocated space for new Windows partitions? See section 8 drive options>Advanced>Extend.

[http://www.sevenforums.com/tutorials/1649-clean-install-windows-7-a.html](http://www.sevenforums.com/tutorials/1649-clean-install-windows-7-a.html)

Regards

Yeah, unfortunately it seems that the resize button is greyed out, so I don't think that will work.

---

### Post by lloyd-connellan on 2016-09-05
So I finally managed to install Windows (10 not 7 in the end), so I thought I'd explain the steps I went through for anyone who might have the same problem for me in case it helps (note that I think the BIGGEST problem I had this whole time was having an SSD and an HDD on the same computer, so these steps might be most useful in those cases.)

As suggested, I backed up all my data that I needed and formatted my HDD. Originally I tried this in Ubuntu using GParted but I found the only method that made Windows recognise it properly was this:
[LIST=1]
[*]Start Windows Installation USB/media
[*]SHIFT-F10 to command line and follow these instructions taken from [http://www.disk-partition.com/articles/we-cannot-create-a-new-partition-1004.html](http://www.disk-partition.com/articles/we-cannot-create-a-new-partition-1004.html) (only do this on an empty drive ofc)
[/LIST]
> Start DISKPART.
Type LIST DISK and identify your SSD disk number (from 0 to n disks).
Type SELECT DISK whatever disk number you have.
Type CLEAN.
Type CREATE PARTITION PRIMARY.
Type ACTIVE.
Type FORMAT FS=NTFS QUICK.
Type ASSIGN.
Type EXIT twice (one to get out of DiskPart, the other to exit the command line tool).

  3. At this point Windows was still having problems recognising my HDD, so it was necessary to PHYSICALLY REMOVE my SSD from my computer (I know) so that it literally only had one available option available to install on (might be also possible to remove the SSD from the boot selection under BIOS but I couldn't find this option). Then it was fine and Windows installed in the normal way.

  4. Once Windows was installed and I reconnected my SSD (in the process blowing dust everywhere and almost causing my HDD to fail), it was necessary to get Ubuntu running again following parts 3-4 of the top answer [here]("http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu?noredirect=1&lq=1"). i.e. You start an Ubuntu USB live disk (try without installing), go to the command line and do the grub-install stuff. This should make booting from Ubuntu or Windows possible if you choose the correct drive to boot from during BIOS (some time I will figure out how to configure the grub menu properly to have Windows and Ubuntu but that day is not today).
  5. Lastly, there is the question of how to reclaim some of the space on the 1TB HDD for Ubuntu to use again. To do this go into Windows and search in the start menu for 'partition manager' and basically follow [these instructions]("http://www.howtogeek.com/101862/how-to-manage-partitions-on-windows-without-downloading-any-other-software/") to create some unallocated space (pretty straightforward). 
  6. The final thing I had to do for some reason (which may or may not actually be a problem in other cases) is to change the write permissions of this leftover space in order to access it without root. I basically did [this]("http://askubuntu.com/questions/74806/how-can-i-change-permissions-on-external-drives"), i.e. 
> 
[LIST=1]
[*]Open "Disk Utility", and look for your device, and click on it. This will let you be sure you know the correct filesystem type and device name for it. In my case, it was 'ext4' and '/dev/sdb1' respectively. Next: Decide what you want to call your thumb drive. I called mine 'USB16-C', but you choose your own name. Before closing Disk Utility, click unmount. And USER should be your login name.
Then run steps 2 to 4 in a terminal window.
[*]sudo mkdir -p /media/USB16-C
[*]sudo mount -t ext4 -o rw /dev/sdb1 /media/USB16-C
[*]sudo chown -R USER:USER /media/USB16-C
[/LIST]


And hopefully that's all you need. Basically it was a massive pain and I recommend if possible you install Windows first and Ubuntu second, since Windows does not play nicely with other OS and will vindictively try to destroy all your hopes and dreams.
P.S. I wouldn't recommend boot-repair for fixing the grub since it basically stopped Windows from working and I had to reinstall it all over again. Just following step 4. was simplest and all that was needed to get it working.

---

