---
title: "Disable Logon"
date: 2021-05-15
forum: General Help
---

### Post by DeadlyOats on 2021-05-15
Hello, Everyone!

So, I've got this ASUS notebook, a tiny little computer.  I don't have anything important on it.  I keep my files in a USB thumb drive.  I don't use it to access the Internet, nor any other network, except for my home wireless network to do updates.  That's it.

I want it to start up speedily and be ready for me to use, even faster than it already is.

My solution?

Do away with logging on.  So, I got it to start up without requiring a password.  That's great!

However, when I lower the screen and close the notebook, it goes to sleep, to conserve battery power, which is nice.

When I open it up and wake it up again, it asks me for a password.

I want it to not do that.  I want it to wake up and be where I left off when I closed the screen and put it to sleep.

How do I do that?

I'm using Kubuntu 20.04.

---

### Post by TheFu on 2021-05-17
I don't know how KDE handle the screen saver timeout, but that's where I'd check.

Besides that, I'm sorry to say that I cannot help you with the not using a password thing, besides to guess that there is a timeout on the screen saver that is being invoked. Just make that longer - like 5 days. That's my guess.  On my Asus laptop, a password is required if it is inactive for 2 hrs (I'm at home all the time too). If I close the lid, it goes into standby.  If I reopen the lid before the screensaver timeout period of 2 hrs, then I am not asked for the password.

You realize that all wifi has security problems, right? Wifi, even at home, should be used with a VPN, if you care about security.  Last week, an issue for nearly all wifi implementations was announced that has been in the code since the 1990s. I doubt that is the last on of those.  At a prior day-job, we were required to use a full VPN whenever any wifi was used, no matter where we were.  They had data security guys who would hunt down wifi-APs in the buildings and confiscate the equipment, since no wifi was approved for use at work.

My laptops use FDE - full encryption - with 2FA. If I change the building they are in, then I completely power them down and have to unlock the disk before they can access any internal storage. I can boot from a flash drive running an ISO with an extra partition  on the flash with either EXT4 or NTFS.  I really would like to use f2fs - which is "flash friendly."  Anyways, my laptops need more security to make me happy.  I don't really trust the internal storage or booting from it when traveling for work. Not everyone has the same security needs.

I've been hacked on trips before, so my security isn't just paranoia. Last time was over bluetooth on a freshly installed and completely updated Ubuntu desktop.  I didn't realize BT was enabled by default. After wiping the system an reloading, I noticed that and have since taken steps to disable BT by removing drivers and management programs, then verifying those are removed at every boot, since patching might bring them back as dependencies.

It can be a dangerous world out there.

---

### Post by ajgreeny on 2021-05-17
Look in the **Power Settings** wherever they are in Kubuntu and make sure the password is not asked for whenever you leave suspend.

It will not matter how the machine gets to suspend, ie the laptop lid switch or using the Suspend button,; the important setting for you to change is how it comes out of suspend mode.

---

### Post by vidtek on 2021-05-17
Go to System-Settings->workspace behaviour->screen locking  look at the options and understand them.   It's one of the first things I do with a new install

Cheers Tony

---

### Post by DeadlyOats on 2021-05-17
> **vidtek said:**
> Go to System-Settings->workspace behaviour->screen locking  look at the options and understand them.   It's one of the first things I do with a new install

Cheers Tony

Thank you all, for your replies.  I appreciate all of your input!

TheFu's information about wifi security is welcome advice.  I'll look into this.

Vidtek's advice took me straight to the fix, however!  Thank you, vidtek!  That's what solved my issue!

---

### Post by vidtek on 2021-05-18
Glad it's sorted for you, please mark this thread as solved.

---

