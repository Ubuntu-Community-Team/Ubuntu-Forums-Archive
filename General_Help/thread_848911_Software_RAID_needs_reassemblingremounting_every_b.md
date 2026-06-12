---
title: "Software RAID needs reassembling/remounting every boot"
date: 2008-07-03
forum: General Help
---

### Post by KillerSiafu on 2008-07-03
I built a media server earlier this year and setup four, 500 gb hard drives in a software RAID using mdadm. I also edited my fstab to include this array. At the time, I was running gutsy.

When I attempted to upgrade my system to hardy, it more or less borked the entire system. I had to do a clean reinstall to get everything working again. To my relief and surprise, when I installed mdadm, edited my fstab, and reassembled the raid array, it worked without a problem.

sudo mdadm --assemble --scan

I then mounted the re-assembled drive and it seemed all was well. However, when I needed to do a reboot, ubuntu errored during loading. It said something similar to failed to load device md0, which is the name of the raid array. It then hung in the terminal so I did a ctrl-d to get to the login / splash screen.

After logging in, I noticed that the directory to which the raid array was mounted was empty. I checked mdadm and the array was not running. I tried doing the same assemble command as above, and it said it was unable to start device md0.

This was pretty confusing to me. So I messed around for awhile and eventually ended up removing and reinstalling mdadm and trying to assemble it again... and it worked.

When I had to reboot again a few days later, the same thing happened, and this solution worked again. 

Of course it is nice to know a solution to the problem, but I would of course prefer that it didn't happen to begin with. Anyone have any suggestions?

---

### Post by fjgaude on 2008-07-04
Interesting... what does the line in your fstab file look like for mounting the /dev/md0 array?

I've had no issues when moving my array from one motheboard to another, from one update to another. Wonder what the difference is?

---

### Post by KillerSiafu on 2008-07-04
My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=e910b19d-a7f7-4f1c-a199-77783b9b5b00 /               ext3    relatime,errors=remount-ro 0       1
UUID=c883f7cc-8fce-44a7-b5a1-66d51c478d11 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/md0 /mnt/raid/ ext3 defaults 1 2

---

### Post by fjgaude on 2008-07-04
**/dev/md0 /mnt/raid/ ext3 defaults 1 2 **

Why do you have that 1 in front of the 2? The 1 means a dump is needed. I don't understand why.

Also did you declare your drives as "**fd**" file type, auto Linux raid, when you create the individual partition on each drive?

The only other issue could be a race problem that md is not ready to assemble when the boot script tells it to.. I will look into what that amounts to and report back.

BTW, to learn more of mdadm see: [http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

---

### Post by KillerSiafu on 2008-07-04
I'm not sure why the 1 is in there... I was following a tutorial on how to setup the software raid and it said to use that line in the fstab. Should this be changed to a 0?

I did setup the drives as type 'fd - linux raid autodetect' when I built the array.

That last issue sounds interesting. Let me know if you find anything on that.

Thanks!

---

### Post by fjgaude on 2008-07-04
> **KillerSiafu said:**
> I'm not sure why the 1 is in there... I was following a tutorial on how to setup the software raid and it said to use that line in the fstab. Should this be changed to a 0?

[COLOR="Blue"]I believe it is standard to have a 0 in that place.[/COLOR]

I did setup the drives as type 'fd - linux raid autodetect' when I built the array.

[COLOR="Blue"]Good[/COLOR].

That last issue sounds interesting. Let me know if you find anything on that.

[COLOR="Blue"]Well here's what a post has suggested, add the sleep line in init:
/usr/share/initramfs-tools/init    # to stop a race condition with md
   145 maybe_break mount
   146 sleep 10
   147 log_begin_msg "Mounting root file system..."
sudo /usr/sbin/update-initramfs -uk all    # run to rebuild the image

Coming from these posts:

[https://bugs.launchpad.net/ubuntu/+b...790/comments/2](https://bugs.launchpad.net/ubuntu/+b...790/comments/2)

[https://bugs.launchpad.net/ubuntu/+s...ols/+bug/79204](https://bugs.launchpad.net/ubuntu/+s...ols/+bug/79204)

Hope some of this helps.[/COLOR]

Thanks!

[COLOR="Blue"]Good luck![/COLOR]

---

### Post by KillerSiafu on 2008-07-05
Thanks again for the help!

I went in and added the sleep 10 and also swapped out the 1 for a 0 in my fstab. Then I rebuilt the image and did a reboot... and it booted up no problem. No more complaining about the raid array. So it must have been that mdadm wasn't ready to assemble the array. At any rate, it appears to be fixed now. Thanks!

---

### Post by fjgaude on 2008-07-05
That 1 could have been the issue too... put it back and see what happens! <sigh>

Not sure what the idea of a dump means in this case... dump memory to disk, or vice versa. <smile>

Glad it is fixed... learn something new everyday, eh?

---

### Post by santhony on 2008-07-10
I'm pulling my darn hair out...   Been trying to build a RAID5 now the past week.. Everything goes fine until I reboot....

Once I reboot, two of my 3 drives are removed from the array.. One goes to spare, the other is totally kicked out...

Anyone have any suggestions??  

Here's my final output:  
santhony@gutsy:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Jul  4 13:28:35 2008
     Raid Level : raid5
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul  4 17:15:55 2008
          State : active, degraded, Not Started
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : ce61f089:73a74ff6:e368bf24:bd0fce41
         Events : 0.52

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       0        0        1      removed
       2       0        0        2      removed

       3       8       16        -      spare   /dev/sdb

---

### Post by fjgaude on 2008-07-11
Well, were any of these drives in a mdadm array before? If so, did you fault them individually then remove individually from the array, then did a zero-superblock on each one?

---

