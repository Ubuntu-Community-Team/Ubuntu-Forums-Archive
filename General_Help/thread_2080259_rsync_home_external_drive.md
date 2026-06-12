---
title: "rsync home external drive"
date: 2012-11-03
forum: General Help
---

### Post by C.S.Cameron on 2012-11-03
Last year, when we went to Sri Lanka, I dd'd my wifes computer to external drive and she booted this from my computer there.

Note: She has been upgrading her computer since 7.04, or there abouts, and it still uses grub classic.

Earlier this year I upgraded the external drive to 12.04 and it seemed to work well.

This year she wants to use the external drive again in Sri Lanka. 

I rsynced her desktop home folder to the external drive and now, when I try to boot, grub only shows choices for 10.04 and will not let me log on.

Can this be fixed?

---

### Post by oldfred on 2012-11-03
Just about anything can be fixed, but sometimes it is better to reinstall. :)

Updating /home should not have changed grub at all. Your /home is all user settings. 

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by C.S.Cameron on 2012-11-03
Thanks Oldfred:
Come to think of it, I also shrank a NTFS partition and expanded the extended and ext3 partitions.
I will give Boot Repair a try and report back.

---

### Post by C.S.Cameron on 2012-11-04
Well Boot-Repair ate my grub and would not install a new one.
Here is the Output:

[http://paste.ubuntu.com/1332975/](http://paste.ubuntu.com/1332975/)

For some reason Boot-Repair thinks the o/s is 10.04, but it has been upgraded to 12.04, the latest kernel in boot is 3.2.0-27 ???

I think I will try to do a fresh install, then insert my wife's current home.

---

### Post by oldfred on 2012-11-04
Fstab is not showing any / (root) ??

And you still have grub legacy in the MBR. I would see if fixing fstab and reinstalling grub2 helps, if you have not reinstalled already.

It looks then like it is half updated, so you may have other issues also.

---

### Post by C.S.Cameron on 2012-11-04
I checked fstab yesterday, it must have gotten rebuilt today.
I just tried installing the latest grub but there were errors.

---

### Post by C.S.Cameron on 2012-11-06
I deleted the Windows and Ubuntu partitions, expanded the extended partition and made new partitions for / and /home and kept swap.
After install I rsynced wifes home to /home using Grsync GUI then chowned the directory.

All is well, at least till she meets Unity.

---

### Post by oldfred on 2012-11-06
Glad you got it solved.

I have Unity in one of my new installs, but just cannot get used to it. It keeps hiding my open screens with the unopened ones and requiring me to use keyboard when in mouse mode. I either want to do everything with mouse, or if using keyboard do everything with keyboard, but not back and forth.

So my 12.04 is gnome-panel. I did not want to try to explain to my wife a new way to do things. She still says XP was better. But all she wants is Firefox, Thunderbird and Picasa. So as long as those three icons are on Desktop she is happy.

---

