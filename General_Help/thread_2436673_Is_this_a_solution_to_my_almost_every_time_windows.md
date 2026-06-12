---
title: "Is this a solution to my almost every time windows upgrade problems?"
date: 2020-02-11
forum: General Help
---

### Post by makem2 on 2020-02-11
I currently have a Windows 10 problem caused by the 'Anniversary' update. However in my case I think it may be possible  to cure this and prevent future problems.

I have a 250 GB SSD installed in a DVD caddy which solely contains xubuntu.

sd1 - fat 32 - /boot/efi
sda2 - ext4 - /
sda3 - ext4 - /home
sda4 - linux-swap

Grub is intact and able to boot windows.

I also have the original 1TB HD on which is Windows 10 plus some data partitions. The user profile is in those data partitions.

sdb1 - ntfs - Basic data partition
sdb2 - EFI - fat32 -system partition
sdb3 - MS - fat32 - reserved partition
sdb4 - ntfs- Basid data partition - Win10
sdb5 - ntfs - unallocated
sdb6 - ntfs - Basic data partition
sdb7 - ext4 - Testing partition

All of the data on both drives is regularly backed up to two remote 1TB HDs

My problem which is that of an inability to get into the desktop, occurs after logging into windows.

A solution for now and future could be:

1. Remove the SSD from the machine
2. Update or repair windows or re-format and install fresh
3. Return the SSD into the machine
4. Reboot

It seems straight forward with some links being lost and maybe grub needs refreshing?

Any thoughts?

---

### Post by mastablasta on 2020-02-11
why would re-installing windows resolve the issue?

---

### Post by makem2 on 2020-02-11
> **mastablasta said:**
> why would re-installing windows resolve the issue?

Because it is a windows problem, nothing to do with xubuntu?

I have tried several of the many methods posted and all that I found did not relate to a dual boot but I tries what I could.

I did suggest, " Update or repair windows or re-format and install fresh"

In that order I suppose. Reinstalling a fresh copy would be a last resort.
 as normally if 'Fs' everything up but this way, maybe not.

---

### Post by yancek on 2020-02-11
Removing the SSD with Xubuntu prior to any windows update seems like a reasonable precaution.  Most of these updates require one or more reboots so setting the windows OS to default in grub.cfg would be a good idea during the update in ase you are not sitting at the computer during one of the reboots.  Simple enough to change it back after the updates.  Another problem I have seen reported here a number of times is that windows rewrites the partition table and does not include any non-windows partitions.  Not sure this would be a problem if you have Xubuntu on a separate drive but...?

---

### Post by makem2 on 2020-02-11
> **yancek said:**
> Removing the SSD with Xubuntu prior to any windows update seems like a reasonable precaution.  Most of these updates require one or more reboots so setting the windows OS to default in grub.cfg would be a good idea during the update in ase you are not sitting at the computer during one of the reboots.  Simple enough to change it back after the updates.  Another problem I have seen reported here a number of times is that windows rewrites the partition table and does not include any non-windows partitions.  Not sure this would be a problem if you have Xubuntu on a separate drive but...?

Thank you.

Except for a testing partition which is formatted ext4, all the partitions on the windows drive are windows based so no problem on rewriting the partition table I would expect.

You say set window as the default in grub.cfg, apart from doing that I always thought grub was located on the drive containing Linux OS which of course will not be there if it is removed, I am unsure how to make changes but will look into it.

I am wondering what I can expect to see after a fresh windows install, when I return the SSD with xubuntu into the DVD drive bay and reboot! If grub is not on the SSD drive then I would just expect windows to boot.

Getting back into xubuntu I can use a hot usb to make grub changes if necessary.

If it is on the SSD then it MAY find the new windows at the same original location but even if not, grub.cfg can be sorted I believe, having done it years ago.

As I make rare use of windows and have another machine (hwmbo)an use that until I get a NEW machine - it really is looking that way as this laptop has seen some service now.

---

### Post by makem2 on 2020-02-11
Well, I think it may be worthwhile charting my progress or non-progress!

I removed the DVD drive caddy with Xubuntu and rebooted. grub started looking for xubuntu and didn't find it where it should be. To be expected of course, but it does show me that grub did not get corrupted and IS not on the SSD drive.

I feel I am close to fixing the existing windows upgrade/install (Aniversary one) that I should persist there first. I get to what it in effect a text version of the desktop shifted halfway up the screen, that's what it looks like anyway and I am able to get to safe mode. I found windows safe mode says the gfx is the latest (I think that is incorrect though) and posters have been suggesting it maybe gfx. And I find sfc /scannow runs but cannot perform what is needed after if finishes the first check for some reason. So,on I go, hating Bill, trying to fix the mess.

I note that windows now includes a Linux subsystem (£250?)

---

### Post by makem2 on 2020-02-12
I ended up giving up with trying to fix windows desktop and instead rolled back to the previous update.

grub was unaffected and the system is back to normal

I di get a thankyou for trying the '**preview**' system whatever that means, as i rolled back.

---

### Post by mastablasta on 2020-02-13
well some of their latest upgrades were really bad causing issues to people even when they rolled back to previous version.

this is because they fired many people that did quality checks and instead rely on the users to do that. but the users are not really that active or their voice is overheard or lost. i don't remember updates causing so many major upgrade issues in winXP era, while the vista updates improved the bad OS and the 7 was really solid in terms of updates (except for the few latest ones). win 10 started out relatively OK but quality dropped quite a bit last year. i mean upgrades deleting user files? it's like someone is forcing beta system to users. luckily i am somewhat shielded with enterprise edition we use at work. unfortunately many games still need windows to run.

---

