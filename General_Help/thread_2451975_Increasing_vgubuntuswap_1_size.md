---
title: "Increasing vgubuntu/swap_1 size"
date: 2020-10-14
forum: General Help
---

### Post by matt_m2 on 2020-10-14
I would like to increase the size of the swap file that Ubuntu 2004 uses by default. I like that it is already a part of the encrypted disk, and that if you were to use this swap for hibernation duties your hibernation state would be protected by the encryption (?).

But is it possible to increase the size of this default swap file? I would need to increase it to about 38Gb as per the Ubuntu documentation for hibernation. 

Any help is greatly appreciated!

---

### Post by TheFu on 2020-10-14
It may be possible.
It may not be possible.

IMHO, hibernation shouldn't be used.  Use standby only if the system isn't moving from a building.  Wasting more than 4.1G for swap just seems **wrong** to me, especially on a system with lots of RAM.

What questions might be asked to determine if a swap file can be increased? 
Actually, the way I'd do it would be to disable swap (**swapoff**), delete the file (sudo rm ....) , create a new file of the appropriate size (there's a fast command for that, but I don't remember it now, sorry) and use the **mkswap** program to format it as swap in the way Linux likes.  If you don't change the name of the file, then you don't need to modify the fstab.

Those steps assume there is sufficient storage to hold the new swap file.

You could also just create a new swap file or swap partition of the size desired, run mkswap and add it to the fstab as swap. The 2 files/partitions would be logically merged by the swap process for you, but I haven't any clue how that may impact hibernation.  When all done, just run **sudo swapon ** and all swap listed in the fstab becomes enabled.

Quick and easy peasy. Of course, when you aren't 100% certain what you are doing, it can take 5x longer.  Don't let the machine hibernate mid-step.

I'm not a fan of swap **files** for a number of reasons, but "easy" beat out the method that's been working and used for 20+ yrs.

---

### Post by matt_m2 on 2020-10-14
Thanks for the response. 

Deleting the swap file ad creating a new one will give you a new UUID that must be update in the fstab right?

With the amount of ram the machine has, I doubt my swap will ever get used for anything other than hibernation. I don't use hibernation all that much, but when I'm out and about and want to conserve battery, it is nice to be able to hibernate and preserve my work session. 

This is a laptop we are talking about. But could you maybe elaborate on why you are opposed to hibernation and swap files? My intention in using a swap file is that it is easy to keep the swap encrypted when it is apart of the partition using luks.

Also I'm specifically talking about increasing the size of the default swap file that Ubuntu 20.04 makes when you decide to encrypt your drive at installation time. 

If it called: 
/dev/vgubuntu/swap_1

and has it's own UUID. However because it is a block device, even if the option to resize it was available, I wouldn't have any space to expand it. 

As the swap is not a partition but rather a swapfile, I'm not sure how to increase the size of it. The partition doesn't need to be resized, only the logical drives within the partition.

---

### Post by CelticWarrior on 2020-10-14
I don't use nor recommend hibernation either for all the reasons TheFu knows much better than I.
I've read somewhere that it needs a swap partition, that it doesn't work with swapfile anyway, but don't quote me on that.

---

### Post by matt_m2 on 2020-10-14
If it is true that hibernation can't use a swapfile, it would could be one thing to help explain why all Linux distros just sort of abandoned hibernation without a word. (or at least a word I can find)

Thanks for your response!

---

### Post by CelticWarrior on 2020-10-14
Windows as well. ;)

---

### Post by TheFu on 2020-10-14
> **matt_m2 said:**
>  
If it called: 
/dev/vgubuntu/swap_1
 

is a logical volume, not a swap file.  It is much more like a swap partition, since logical volumes can almost always be considered to be like partitions, except when it comes time to change things. 

How much do you really want this?

I ask that question because you'll need to learn about an intermediate administration skill to be successful and it is very likely that there isn't any space left over if you did the default installation using 
[LIST]
[*]LVM and
[*]encryption
[/LIST]

Don't get me wrong, I use this and it is extremely flexible, if you change the LV sizes immediately after the installation. If you wait too long, then the "root" LV will become too full of stuff and we cannot safely resize (reduce it).
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) has my layout on an encrypted laptop.
I show all the commands to be run to provide the information we need.  I'd prefer this command:
**lsblk -o name,size,type,fstype,mountpoint**  be used now for the similar one in that post.

If your '**vgs**' command shows unused space, then this will be really easy.  If it doesn't, then this is non-trivial.

---

### Post by matt_m2 on 2020-10-14
Could you share why you discourage hibernation? 

Thank you once again for the link!

To answer the question of how much I want this, the answer would be, I really do want it, if using a logical drive as a swap will work with hibernation and if using hibernation doesn't seriously impact system performance or privacy.

---

### Post by CelticWarrior on 2020-10-14
Security issues in a nutshell. I'm sure if you ask nicely TheFu will unpack the nutshell.

But really, in this day and age, do you really think the battery saving difference between suspension and hibernation is anything but negligible? Do you intend to hibernate for days/weeks, as that's the only scenario where you may notice the difference? I don't think so...

---

### Post by matt_m2 on 2020-10-14
My experience has been that if you suspend your laptop for 3 days, when you come back the thing is dead. I think if you are using your laptop every single day, then it is fine, but I do find it annoying that if I don't use the laptop for a day or two when I come back the battery that is significantly diminished. 

Hibernation just take the angst away. You know? 

Still I could get used to life without it.

---

### Post by CelticWarrior on 2020-10-14
There are other ways to "keep the session" without hibernating but shutting down. Some DEs used to do that by default or had a very easy to toggle on/off setting just for that purpose. And shutting down is actually the proper way to take advantage of encryption.

In the past people used suspension and/or hibernation because it was much faster to wake up than cold booting. Nowadays not so much. I always shutdown (most cases) or use the automatic suspension by closing down the lid (occasionally).

---

### Post by TheFu on 2020-10-14
> **matt_m2 said:**
> My experience has been that if you suspend your laptop for 3 days, when you come back the thing is dead. I think if you are using your laptop every single day, then it is fine, but I do find it annoying that I don't use the laptop for a day or two and come back to battery that is diminished. 

Hibernation just take the angst away. You know? 

Still I could get used to it.

I charge my laptop nightly, so it ins't an issue. Plus, if standby is working and there's a full battery, it should last more than just a few days.  How old is this thing?  My 2015 chromebook with Ubuntu-Mate would last for a week or 3.  But it didn't have a spinning HDD and doesn't wake up to look and doesn't have a discrete GPU.  If you have the mouse as the anti-sleep activation - don't do that.  Make the out-of-standby require a keystroke, even better, the power button.

Encrypted storage is only safe when it is at rest. From the time we type in the LUKS decryption passphrase  until we shutdown the computer, there is effectively no encryption.

Hibernation **isn't** "at rest". 
Standby **isn't** "at rest."  
Completely shutdown **is** "at rest."  

So, if you've got website logged in or left your password manager running, unlocked, it is very likely all those credentials are stored in the swap. Anyone with root access can scan the process memory (doesn't matter if that is swapped or not) and probably find things that are logins.  Do a google search and try it out with your password manager while it is running.  The RAM for every process is accessible under /proc/. 

My trade-off for using standby is this.  If I'm leaving the building, I shut down.  That's with or without the laptop.  Properly secured storage, especially if you setup 2FA with a challenge-response key is very secure - WHEN AT REST.

Hope this helps.

---

