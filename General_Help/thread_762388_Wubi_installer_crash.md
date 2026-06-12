---
title: "Wubi installer crash?"
date: 2008-04-22
forum: General Help
---

### Post by chroniton on 2008-04-22
I just downloaded the latest Ubuntu iso (8.04 RC) and Wubi (rev 494).  I run the Wubi setup, select my drive & size, enter my password, and hit next.  The installer says checking installation files / calculating checksums.

The progress bar makes it all the way through, 100% on the checksums.  Next it says Creating Image / Initializing.  I only see it for a split second, because the program crashes and disappears.    No matter how many times I run it, or what options I choose, it always does the same thing at the same time.

Any ideas?

(Windows XP 32-bit w/SP2 on Athlon 64 x2 3800+ dual core, 2 GB memory)

---

### Post by ago on 2008-04-22
can you please post the wubi log in your tmp user folder (%temp%)

---

### Post by ago on 2008-04-22
Please try rev 495, but do post the rev 494 log anyway!

---

### Post by chroniton on 2008-04-22
Ok, here's the log file.

---

### Post by chroniton on 2008-04-22
Okay, I tried rev 495.  I no longer get the "Can't open registry key!" errors in the log, but other than that the logs are identical, and the crash happens at the same spot.

---

### Post by ago on 2008-04-22
Run wubi with the argument "--skipmd5check"
That is only a workaround, I am afraid I will not be able to do a proper fix before final release (possibly the stand-alone will change).

---

### Post by chroniton on 2008-04-22
well, adding --skipmd5check certainly made it crash faster ;)

From the end of the log:

Found a good ISO: Ubuntu 8.04 "Hardy Heron" - Release Candidate i386 (20080417.1)
Found CD T:
Found CD cddrive=T:
Installing in automatic mode from CD
CheckCD
check_internet_connection
Dialer online
connected
skipmd5check specified, skipping CheckCD
CD2ISO J:\ubuntu\install\installation.iso

---

### Post by ago on 2008-04-22
Ok it ooks like the CD2ISO plugin is not compatible with your machine (could have been a different issue). I will have to add some logging there. Can you try using a different CD and/or an ISO (without the CD inserted)?

---

### Post by ago on 2008-04-22
Please subscribe to this thread, so once I have the logging ready you will be notified and will be able to help with testing.

---

### Post by chroniton on 2008-04-22
> **ago said:**
> Ok it ooks like the CD2ISO plugin is not compatible with your machine (could have been a different issue). I will have to add some logging there. Can you try using a different CD and/or an ISO (without the CD inserted)?

Hmmm...  Could the problem be that I'm using a DVD and not a CD?  The ISO is named: ubuntu-8.04-rc-dvd-i386.iso  (3.74 GB)

---

### Post by ago on 2008-04-22
> **chroniton said:**
> Hmmm...  Could the problem be that I'm using a DVD and not a CD?  The ISO is named: ubuntu-8.04-rc-dvd-i386.iso  (3.74 GB)

Could you please try with a CD ISO burnt on a CD media. 
Let me know as soon as you are done!

---

### Post by chroniton on 2008-04-22
It made it further... hung on the "creating virtual disks" step for quite awhile.  Then it finally finished.  I haven't rebooted yet to try it out.

So the issue seems to be related to using a DVD iso vs. the CD iso.

---

### Post by chroniton on 2008-04-22
Okay, so I rebooted and chose Ubuntu.  It booted into the Ubuntu GUI and performed some setup, then rebooted by itself.  The next time it comes up, it hangs in GRUB with this error:

> 
root(hd4,0)/ubuntu/disks
Error 21: Selected disk does not exist.


I guess the "hd4" is wrong?  How do I find the right one and edit the grub configuration from windows?

---

### Post by ago on 2008-04-22
[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

see third paragraph, you might wanto try any number from 0 to 4

---

### Post by chroniton on 2008-04-22
Okay, setting it to root(hd1,0) *seemed* to work.  It starts booting without an error... shows the Ubuntu splash screen and the progress meter.  Then, it just drops me to a shell.  The shell says "Busy Box" and "initramfs".  I can't seem to get from that shell into the Ubuntu gui.

---

### Post by ago on 2008-04-22
(hd1,0) is the first partition on the second hard disk. Is that where you installed wubi? If you happen to have ANOTHER linux installation in (hd0,1), then you will not be able to boot off that.

To confirm that type: uname -r
It should be 2.6.24.16+ and the arch should match the one you used for installation.

You can also try to choose the second option to boot (rescue mode) and add "debug" to the kernel line. See if there is any interesting message (log will be under /tmp).

---

### Post by chroniton on 2008-04-22
It's a little hard for me to guess at drive numbers.  I have four drives tied into a RAID 10 array, and two that are standalone.  None of them have any trace of linux on them except for the "ubuntu" folder that Wubi installed on the first partition of the first standalone drive.  (hd1,0) is probably correct if you count the raid set as a single drive.  If you count them separately, you'd get (hd4,0) which is what we had before that didn't work.

---

### Post by ago on 2008-04-22
then do as suggested in the last paragraph

---

### Post by chroniton on 2008-04-23
I tried the rescue option, but I didn't see anything obvious.  Thanks for your help.. but I'm out of patience for this problem.  I have to give up and just keep windows.

---

