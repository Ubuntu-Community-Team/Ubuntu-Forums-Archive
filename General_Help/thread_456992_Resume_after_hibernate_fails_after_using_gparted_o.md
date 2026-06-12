---
title: "Resume after hibernate fails after using gparted on swap partition"
date: 2007-05-28
forum: General Help
---

### Post by sllewji on 2007-05-28
I am using Feisty and have recently enlarged my swap partition using gparted. Subsequently, when attempting to resume after a hibernation, the system just starts as normal instead of resuming the hibernated state.

Although I am a bit of a Linux newbie, I have done some investigation, and (rightly or wrongly) come to the conclusion that the startup process defined in the initrd appears to have the hardcoded UUID for my previous swap partition in the /conf/conf.d/resume file, and that this may be why the hibernate resume no longer works.

Now if I have got this right how should I resolve this? Is there a  mechanism in Ubuntu which will automatically update the UUID in the initrd or do I have to manually update the resume file in the initrd file with the new UUID.

Any help much appreciated.

---

### Post by sllewji on 2007-05-28
Though I had it sorted.

Updated the UUID of the new swap partition in /etc/initramfs-tools/confd/resume then ran the update-initramfs script.
New initrd created with correct UUID for swap partition.
Still no resume from hibernate.

Tried updating resume file to include /devsda3 instead of th UUID, then updating initrd using update-initramfs.
KINIT then tried to locate hibernate state on /dev/sda3 but didn't succeed.

Also noticed that the newly generated initrd was not loger able to resume from suspend, so replaced it with original backup (with out-of-date swap UUID)

Now back to square one. I can hibernate but machine will not resume.

Anyone help - please

---

### Post by sllewji on 2007-05-29
Well no responses from the community so far - but I'll continue to post my findings in the hope that someone else may get some benefit if they find themselves in a similar situation.

I left the reference to /dev/sda3 in the /etc/initramfs-tools/conf.d/resume file whilst carrying out the kernel upgrade to 2.6.2.16 as suggested by the upgrade manager.

After the upgrade Ubuntu completely failed to boot into either 2.6.2.15 or 2.6.2.16.

For some reason the upgrade process changed /boot/grub/menu.lst root entries to (hd0,0) instead of (hd0,1).
I changed them back and Ubuntu is now booting again - and hibernate works as well!

So it may be that the device reference in the resume file in the initrd image is critical to the correct function of hibernate/resume - but it does seem a little strange that the resume process relies on a hardcoded device reference rather than just looking for a saved state in whatever the current swap partition is during boot.

---

### Post by sllewji on 2007-05-30
For whoever may be interested;

I now have the system fully operational again and using the UUIDs that Fiesty prefers.

So here's the method I (eventually) used to get it working;

After changing my swap partition (by using mkswap for example) I found that the UUID of the swap volume changed. This resulted in me being unable to resume from a hibernated state because the UUID of my original swap volume was hardcoded and stored in a file in initrd which boots the system and tells it where to look for the hibernated state.

To recover from this I ran 'sudo vol_id /dev/sda3' to get the UUID of the new swap parition (change the /dev/sda3 to whatever your swap parition is) make a note of it.

Next I edited the file '/etc/initramfs-tools/conf.d/resume' (ie gksudo gedit /etc/initramfs-tools/conf.d/resume) and updated the line that begins 'RESUME=UUID= .... ' with the new swap partition UUID.

Lastly, I ran 'sudo update-initramfs -u' to update the intitrd with the new UUID.

Upon reboot KINIT then looked at the new swap parition for a hibernate state to resume from before booting.

Hope this helps someone.

---

### Post by schport on 2007-07-08
Thank you so much for your hard work to solve this issue!  =D>

This is exactly the problem that I was having.

I really appreciate your efforts to document the solution you found in an easy to understand way.

---

### Post by fensterkreuz on 2007-12-15
Thank you very much for your path to solve the swap-hibernate problem. This situtation occured after migrating to a new hard drive via dd. Your help in this was very useful!

---

### Post by ACGarland on 2008-04-29
I would also like to say a big THANK YOU for posting your solution as it also fixed the problem I was having.

---

