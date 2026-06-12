---
title: "Check my fstab edit for auto-mounting a hard drive at startup?"
date: 2017-01-23
forum: General Help
---

### Post by AwaitingUserInput on 2017-01-23
I just installed Kubuntu 16.04. It is an upgrade from an old installation of Linux Mint.

I have several internal hard drives that I would like to have automatically mounted when I start or reboot the computer. Some of the drives have multiple partitions. I'd like to mount them at /mnt/ rather than in /media/username and keep the /media/username mount point for things like USB drives, SD cards and more temporary stuff. Is there anything wrong with using /mnt as a mount point?

I have not changed /etc/fstab yet because I don't want to screw it up. Here is the result for 1 of the drives when I run "blkid" 

```
/dev/sdb1: UUID="ff82962c-054e-4486-9cad-d2f8801f942e" TYPE="ext3" PARTUUID="00069a28-01"

```


Using that as an example, how does this look for an fstab edit?

```
UUID=ff82962c-054e-4486-9cad-d2f8801f942e       /mnt/WD500GB   ext3    defaults        0       2

```

Here I am setting the mountpoint to /mnt/WD500GB because this is my only 500 GB Western Digital hard drive, so I will always know what one it is.

Am I doing something that I will regret later? Should I go about this another way?

I just want to check before I go too far down the road setting up my new system.

---

### Post by yancek on 2017-01-23
> Is there anything wrong with using /mnt as a mount point?

No.  That is the standard location for permanent mount points.  If you do not have your external drives always attached when you have fstab entries for them, it will delay boot with warning messages.  Your fstab entry looks correct.  Depending upon what/how you want to use the partitions, you might want different parameters rather than default.

---

### Post by AwaitingUserInput on 2017-01-24
Thanks for looking. One more question: do I need to do ```
sudo mkdir /mnt/mountpoint
``` in order for fstab to mount a hard drive there? Or does the OS create the mount point automatically?

---

### Post by oldfred on 2017-01-24
You have to make mount points first.
sudo mkdir /mnt/WD500GB

More examples.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 

Always backup fstab and check if correct before rebooting.

 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

### Post by Dennis N on 2017-01-24
> **AwaitingUserInput said:**
> One more question: do I need to do ```
sudo mkdir /mnt/mountpoint
``` in order for fstab to mount a hard drive there? Or does the OS create the mount point automatically?

It depends on the OS you are using. For Ubuntu and family, I once forgot to create the mount point when setting up a partition to be mounted at a subdirectory of /mnt, but found Ubuntu created the necessary directory for me. Since then, I have done it several more times and confirmed this. Of course, you can make it first too.

But, on the other hand, with Korora (and probably its parent, Fedora) I discovered this doesn't work -  you need to create the mount point first (or you end up in "Emergency Mode").

Actual entry for mounting (first line is just a comment):

```
# Label=Common-Files /dev/sda4
UUID=d97e2feb-1bf6-429b-bba5-943264ec1474 /mnt/Common-Files ext4 defaults 0 2

```

---

### Post by AwaitingUserInput on 2017-01-25
Thanks for all the help. The templates oldfred linked in [this post]("https://ubuntuforums.org/showthread.php?t=1983336&p=11955166#post11955166") did the trick no problem.

One thing that surprised me was that on a drive with multiple partitions, each partition had its own UUID. I initially thought that each DRIVE would have a UUID and was wondering how to mount the partitions, but the problem solved itself.

Thanks again. I will mark this thread as "solved."

---

