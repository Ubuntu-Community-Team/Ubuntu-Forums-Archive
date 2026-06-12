---
title: "Restore to different media"
date: 2020-10-08
forum: General Help
---

### Post by mjutras2 on 2020-10-08
I am not fluent with Linux, I feel like my learning curve lasts for a life time, my fault for being on MS for so long.

I have installed Lubuntu 20.04 with a bunch of apps including VirtualBox and a number of VMs and then I did a snapshot with Timeshift.
My original installation is on a Sata 2.0 SSD 2.5" drive.
Now I would like to replace my 2.5 drive with an mSata card since it takes less space and dissipates less heat.
Since it is a different media, if I install a basic Lubuntu and Timeshift on the mSata, will the restore work?

Thanks.

Michel

---

### Post by gdesilva on 2020-10-08
I think it would be simpler to do the following - IF your mSata drive is equal or bigger in size to your 2.5" drive;

1. Boot the system with LiveUSB/LiveDVD - open terminal and sudo -s <return> to become administrator
2. dd if=/dev/<2.5" drive> of=/dev/<msata> bs=4M status=progress           - this will copy the entire content of 2.5" to mSata
3. Once completed, do blkid command to work out the universal device ID of your disks
4. edit /etc/fstab file on the mSata drive and replace 2.5" UUID references with ones for mSata drive and save the file
5. reboot the system by selecting the mSata drive as the boot device.

---

### Post by mjutras2 on 2020-10-09
Thanks for the quick response and the procedure.
I will give this a try.

---

### Post by mjutras2 on 2020-10-10
ok my source disk is 500GB and destination disk is 256GB. I figured it would work because I only have 30GB of data but it looks like dd does a full partition copy.
It is obvious that I need to resize my source disk to the size or smaller than the destination disk. Going to the GUI I see KDE Partition Manager but I cannot resize unless I unmount the partition.
I am seeing different responses on the subject on the web so I am unsure.
If I boot from dev/sdc can I open KDE from the GUI, unmound, resize and then mount without crashing or loosing data?

UPDATE: I quickly realised I had follow your 1st point: Boot the system with LiveUSB so that is what I did.
I was able to resize the current partition down to 232Gib as the mSata is 238Gib. 
launched:  dd if=/dev/sdb1 of=/dev/sda bs=4M status=progress

Restarted from the original SSD drive and I can see the mSata but I can't access it to go and edit fstab.

Anyhow, blkid is showing this:
/dev/sda: UUID="9016eee0-844a-4519-886d-9a642c870e4c" TYPE="ext4"
/dev/sdb1: UUID="9016eee0-844a-4519-886d-9a642c870e4c" TYPE="ext4" PARTUUID="e7d6a702-01"

I want to take out /dev/sdb1 and keep /dev/sda

the fstab file contains this:
UUID=9016eee0-844a-4519-886d-9a642c870e4c /              ext4    defaults,discard 0 1
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0

So what is it I need to modify?

I'm stuck again...

---

### Post by tea for one on 2020-10-10
Before attempting to re-size partitions, please make sure that you have **backups** of your data.

You can only manipulate partitions that are not in use i.e.unmounted.

You cannot clone/dd a larger partition into a smaller partition.

A [COLOR="#0000FF"]live[/COLOR] session will allow you to adjust partitions.

There is no guarantee that you will not lose data when partitioning, hence backups are essential.

---

### Post by tea for one on 2020-10-10
> launched: dd if=/dev/sdb1 of=/dev/sda bs=4M status=progress

sdb1 is a partition
sda is a device (not a partition)

In your position, I would use Clonezilla [https://clonezilla.org/](https://clonezilla.org/).

Have a look at the operations [COLOR="#0000FF"]device to device[/COLOR] or [COLOR="#0000FF"]partition to partition[/COLOR].

---

### Post by TheFu on 2020-10-10
To clone a partition and restore to a smaller partition, look at either **fsarchiver** or use file-based tools like **rsync**. Regardless, the new disk must have the partitions pre-made. After the mirror/cloning,  fix the fstab. Might be necessary to reinstall grub (grub-install) and update grub (update-grub) too.

But really, the best answer is to use the plan you have with whatever backup tool was already selected. This is a perfect opportunity to test that.  If the current backup tool doesn't meet your needs, FIND A BETTER TOOL!

IMHO.

---

### Post by GhX6GZMB on 2020-10-10
It's a bit more involved than that.

Timeshift is basically a system backup tool (using rsync) which will restore all the setups and configurations, but it will also backup your $HOME directories if you like.
Be certain to select this option under the "Settings/Users" menu when creating the backup.

I wrote a recipe on how to do the bare bones install/restore restore, you'll find it here:

[https://ubuntuforums.org/showthread.php?t=2447108](https://ubuntuforums.org/showthread.php?t=2447108)


Cheers.

---

### Post by gdesilva on 2020-10-11
Given your source disk is bigger than the mSata drive, using dd might not be  the best solution as this means even if you copy just the partition then you have the issue of having to re-install grub bootloader etc. However, if you want to continue down this path I would do the following....

1. Boot using LiveUSB/LiveDVD
2. Delete existing partitions on mSata drive and create a new ext4 partition.
3. Since you have already shrunk the partition in the source drive to match the size of the mSata drive, now you can copy the contents to the newly created partition on mSata drive. As @Tear for One picked up, the command should be
   dd if=/dev/sda1 of=/dev/sdb1 bs=4M status=progress       ##### where /dev/sda1 is your source partition and /dev/sdb1 is your partition on the mSata drive
4. Now you should be able to see both /dev/sda1 and /dev/sdb1 partitions - run mount command to find out where the file systems are mounted and note them down. If not mounted then you would need to mount them as follows;

    mkdir /mnt/orig     ## create a mount point for the first drive
    mount /dev/sda1 /mnt/orig      # mount your original drive under /mnt/orig
    mkdir /mnt/msata   ## create a mount point for the mSata drive
    mount /dev/sdb1 /mnt/msata  # mount the new partition

5. run blkid - this will list the UUID strings for each of the partitions on your system.

6. now edit /mnt/msata/etc/fstab and replace the UUID string (the one after the UUID= WITHOUT the "") of the original partition with the UUID string of the mSata partition. Save the file.

7. If you want to remove the original disk, it is imperative that you write the grub bootloader information on the mSata drive. To do this, run the following command

    grub-install --boot-directory=/mnt/orig/boot /dev/sdb    ## note that there is no number after sdb this time. This command tells to write the grub bootloader into mSata drive using already
    existing  grub config files in the original drive.

8. shutdown the LiveUSB session and remove the original drive

9. Reboot.


Hope I covered all the details - apologies if I missed anything. Note this is assuming that you are NOT using  UEFI to boot - let us know if you are as the process will need to be slightly modified!

---

### Post by mjutras2 on 2020-10-11
@gdesilva 
I followed your steps 1,2,3.
at step 4 running the mount command showed an overwhelming list (to me) that I could not interpret so I proceeded to your next step to create mounting points and mounted both.
My original disk shrunk to 232 Gib is /dev/sdb1
My mSata disk is /dev/sda1 
but when I ran blkid it showed me one line for /dev/sdb1 and a second line for /dev/sdc1 (I believe is the liveUSB)
However, opening KDE Partition Manager showed /dev/sda1 as mounted.

When comparing between /mnt/msata/etc/fstab and /mnt/orig/etc/fstab they are identical (which is obvious since one is the copy of the other)

I removed the liveUSB and restarted form the original disk and now when I run blkid I get this:

/dev/sda1: UUID="9016eee0-844a-4519-886d-9a642c870e4c" TYPE="ext4" PARTUUID="5108ac39-57bd-e04b-a95a-eee996f79030"
/dev/sdb1: UUID="9016eee0-844a-4519-886d-9a642c870e4c" TYPE="ext4" PARTUUID="e7d6a702-01"

Looking at /etc/fstab I have this:
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=9016eee0-844a-4519-886d-9a642c870e4c /              ext4    defaults,discard 0 1
tmpfs                                     /tmp           tmpfs   defaults,noatime,mode=1777 0 0

I do not understand what I need to change in this file since the UUID is identical for both.

I don't know if I am getting closer but if I am, I realized I forgot your step #7, can this be run from the original disk? (without the need to restart from liveUSB)?

Sorry, i feel really dumb with all my questions and taking so much time trying to do something I would do in a few minutes under MS.

---

### Post by TheFu on 2020-10-11
When we "clone" an entire HDD, the UUIDs get cloned too.  The fix is to force one of them to change. Bad things happen if two partitions have the same UUID connected to the same system at file system mount time.  

I'd google "force uuid change" for the command.  [https://askubuntu.com/questions/132079/how-do-i-change-uuid-of-a-disk-to-whatever-i-want](https://askubuntu.com/questions/132079/how-do-i-change-uuid-of-a-disk-to-whatever-i-want) is a reputable answer. Use **tune2fs** with an option.
```
sudo tune2fs /dev/{device} -U random
```

I'd force the change on the new storage and leave the old storage alone.  Then update the fstab that points to the new storage.

---

### Post by mjutras2 on 2020-10-11
When I run sudo tune2fs /dev/sda1 -U random

I get:
This operation requires a freshly checked filesystem.
Please run e2fsck -f on the filesystem.

When I run sudo e2fsck -f /dev/sda1

I get:
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.

When I run sudo umount /dev/sda1

I get:
umount: /: target is busy.

At this point, my understanding is since both drives have the same UUID, they are both busy and I need to go from liveUSB...
I hope I am making progress, life is not that long.

---

### Post by TheFu on 2020-10-11
Ah ... and you were doing well.

When you cloned the disk, it wasn't quiesced.  That was bad.  I'd do it again from unmounted source and target storage to prevent issues.  You could boot into "Rescue Mode" .... when the grub menu shows up, pick "Advanced", then pick "rescue.  Be 100% certain that both disks aren't connect when you do this, since they have the same UUID, it would be easy to pick the wrong disk/partition. There is an option on the blue menu.  Run fsck on all file systems.  Pick that.

Next time you clone anything, boot into a **Try Ubuntu** flash drive.  All these commands should have been run from an OS on  alternate media - i.e. an external flash drive.

I keep a USB flash drive around with my currently installed ubuntu version (any of the desktops from that release). Then I can boot into the "Try Ubuntu" environment to handle things like this.  We can run fsck, mess with partitioning, resize, reduce, and fix refuse-to-boot situations from this "try ubuntu" environment.

---

### Post by mjutras2 on 2020-10-11
@TheFu

I have advanced a bit before I could read your response.

I rebooted to liveUSB and was able to run tune2fs /dev/sda1 -U random
rebooted again with liveUSB and blkid is now giving me a new UUID for sda1

I then modified fstab on new mSata disk

But trying to install grub I get this:

lubuntu@lubuntu:~$ sudo grub-install --boot-directory=/mnt/orig/boot /dev/sda
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: error: embedding is not possible, but this is required for cross-disk install.
lubuntu@lubuntu:~$


UPDATE: 
The above message lead me to think it is booting in UEFI but I did:
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
and the response is: "Legacy boot on HDD"

---

### Post by GhX6GZMB on 2020-10-11
You need to run from a live boot to manipulate the UUIDs, as the file system UUID(s) you want to change must be unmounted.

@TheFu: the Lubuntu installer does not offer "Try Ubuntu", it's called "Start Lubuntu. Just for reference.

---

### Post by mjutras2 on 2020-10-11
I am about to toss everything out the window...

I downloaded clonezilla, booted with live clonezilla and picked pretty much the defaults or beginner options, completed succesfully but still not booting from the msata drive and now the msata UUID is back to the same as the original disk.
I guess my options now are to keep the 500GB SSD or spend another $100 and purchase another msata disk that is 500Gb or bigger...
Or do I have other simple options?

---

### Post by GhX6GZMB on 2020-10-11
The problem is, that every contributor here rides her/his own hobby horse: dd, clonezilla, whatever. And the users riding their hobby horse DO NOT RUN LUBUNTU.

Think about it. I run Lubuntu and have been where you are several times. And have resolved it.

Apparently you're now about to invest more money due to bad advice? Please, no!

This is solvable.

The solution I linked to in post #8 works, but was unfortunately badmouthed by TheFu for no apparent reason and with incomplete knowledge. TheFu should  explain that her/himself.

---

### Post by tea for one on 2020-10-11
> **mjutras2 said:**
> I am about to toss everything out the window...

I downloaded clonezilla, booted with live clonezilla and picked pretty much the defaults or beginner options, completed succesfully but still not booting from the msata drive and now the msata UUID is back to the same as the original disk.
I guess my options now are to keep the 500GB SSD or spend another $100 and purchase another msata disk that is 500Gb or bigger...
Or do I have other simple options?

After you have completed the clone successfully, you disable, de-activate or remove your source disk and use your target disk. 

Then you decide what you want to do with the source disk e.g reformat and use as a back up.

---

### Post by mjutras2 on 2020-10-11
I am still going at it...

I have removed my original disk, did a fresh install on the mSata and tried to restore from the latest Timeshift snapshot and that didn't go well... after the restore it rebooted with still the fresh install and then I tried to reboot again but it crashed.
What good is Timeshift for?
I had it setup using RSYNC and selected to include root and user files.

I connected my old drive back and I had half the applications and the fresh install background. I had to disconnect the mSata to get back on track.

So I am back to square 1.
At this point I think I will just reinstall everything manually. It is a full day of work but it will be faster than keep trying to clone the drive, I have lost about 4 days trying.

---

### Post by TheFu on 2020-10-12
A quick tip to deal with the package reinstallation.

Step 1: save a list of installed packages somewhere - I'd put those lists into your HOME.
```
dpkg --get-selections  > $local_backup/dpkg.list
apt-mark showauto | tee $local_backup/apt-mark.auto
apt-mark showmanual | tee $local_backup/apt-mark.manual
```

Step 2: backup your $HOME

Step 3: Do a fresh install on the new storage

Step 4: restore your $HOME

Step 5: Using the list of packages, feed that into apt-get to install them with 1 command:
```
sudo apt-get install -y $(< $local_backup/apt-mark.manual)
```

That should get most of "your system" back the way it was in 30-45 minutes.
I started a more detailed blog article about this with commands, but because I haven't tested it and it is more than just a few commands, I didn't feel comfortable posting it here.

Extra credit: backup /etc/ too.  There are a few files down there that get modified which are useful to have later, but we can't just restore /etc/ because that will break a new install. The restoration needs to be selective, perhaps 10 files.  /etc/ is just config files and relatively small. Backing it up should be less than 5 seconds.

---

### Post by mjutras2 on 2020-10-12
@Thefu

Thanks for the guidance but this morning I woke up early and with lots of courage and coffee I did a fresh install and reinstalled my apps. I just finished (almost) and it took me 6 hours.
Knowing I have a good configuration on my original drive, I figured if I don't succeed I will just put back the other drive and forget about the hole thing.

This box is mainly to run some VMs such as PiHOLE, HASSIO, Unifi controller and 3CX SBC. It is running headless on a shelf and if I need to manage it I use TeamViewer (because GUI is quicker that command line for VirtualBox) As you can imagine when this is down, I loose my phones, my lights and I hear my wife with no filters when Internet goes out.

I tried to uninstall almost everything I don't need to make room and use the processes for only what is needed but it looks like I uninstalled the GUI version of the packages manager by mistake. I forgot what it was called. How do I bring it back?
I think that will be my last question on this thread.

---

### Post by TheFu on 2020-10-12
> **mjutras2 said:**
>  Thanks for the guidance but this morning I woke up early and with lots of courage and coffee I did a fresh install and reinstalled my apps. I just finished (almost) and it took me 6 hours.
Knowing I have a good configuration on my original drive, I figured if I don't succeed I will just put back the other drive and forget about the hole thing.

Ouch. We've all been there. We try so hard here to help people avoid the pains. Sometimes we miss that target. We struggle here with many different skill levels (sending and receiving) and feeding just enough information, just in time to be useful.

> **mjutras2 said:**
> 
This box is mainly to run some VMs such as PiHOLE, HASSIO, Unifi controller and 3CX SBC. It is running headless on a shelf and if I need to manage it I use TeamViewer (because GUI is quicker that command line for VirtualBox) As you can imagine when this is down, I loose my phones, my lights and I hear my wife with no filters when Internet goes out.

The pihole would be the worse, if that's your only DNS for the LAN. But before you take down the pi-hole, just add 1.1.1.1 as the secondary DNS for the systems you want to keep working, assuming a redundant pi-hole isn't possible.

> **mjutras2 said:**
> 
I tried to uninstall almost everything I don't need to make room and use the processes for only what is needed but it looks like I uninstalled the GUI version of the packages manager by mistake. I forgot what it was called. How do I bring it back?
I think that will be my last question on this thread.
**sudo apt install synaptic**?  I'm guessing. There are a few different package managers.

Applications and packages really don't use that much storage.  It is almost always data that is the problem, IME. Only snap packages are bloated.

---

### Post by mjutras2 on 2020-10-12
Great! thanks for the info, Synaptic is perfect. I have reached full expected results. Had a rough time but I learned from it.

Thanks to everyone for your help, this forum is awesome.

Cheers!

---

