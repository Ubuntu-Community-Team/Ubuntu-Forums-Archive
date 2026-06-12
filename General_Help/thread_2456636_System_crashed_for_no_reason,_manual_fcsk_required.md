---
title: "System crashed for no reason, manual fcsk required"
date: 2021-01-15
forum: General Help
---

### Post by abelito8 on 2021-01-15
did not add any command or touch the system, was not functioning so I just rebooted the computer and could not get in, got strange message (cannot take screenshot, I had to get a pic). I tried with recovery mode and I have the same message (see attachment). I can of course reinstall everything but can't this be fixed manually (like using a startup usb?) it's the second time since October and the computer is from March 2020...so I suspect some hardware issue also...

---

### Post by guiverc on 2021-01-15
I would suggest booting a *live* system (such as Ubuntu install media, and use "*Try Ubuntu*"), and performing the `fsck` (*file-system check*) it says in the error message.

It's easier from a *live* system, as the disk won't be used, and thus you don't need to worry about unmounting partitions etc. These errors can occur for a number of reasons (surge or fluctuation in power without a filter being used, etc) so I don't worry about the rare/very-occasional occurrence  (your fridge may have turned on the same microsecond someone started a kettle causing a minute/temporary drop in power), but should it start occurring regularly, check out your hardware  (*clue something maybe starting to fail etc*). 

You don't need to use the same release, I'd opt for a modern release (over something very old), but it can be a different *flavor* too. If the `fsck` detects & fixes errors, I'd expect a normal boot on next try.

---

### Post by HermanAB on 2021-01-16
Linux is extremely reliable software, but the computer hardware can malfunction due to various reasons, from power fluctuations to cosmic rays.  A laptop computer has a built-in battery but a desktop machine doesn’t.  So if you ever see your lights dim momentarily, then you should probably invest in a small UPS for your desktop.

---

### Post by Paddy Landau on 2021-01-16
There is an easy way to get the system to run fsck on your system disk. Enter  the following command&#8230;
```
sudo touch /forcefsck
```
&#8230; and then reboot. The system will run fsck as part of the boot process. No need for a live disk.

---

### Post by abelito8 on 2021-01-16
thank you, I tried and it's asking who is sudo...does not recognise the command, I used it without sudo and did not perform the action...

---

### Post by abelito8 on 2021-01-16
thank you, I was on a laptop but I had to turn it off brutally because it had frozen...perhaps this, but definitely not the desktop issue

---

### Post by abelito8 on 2021-01-16
thank you, I tried and even when opening the live cd (USB) it warns me that the error already occurred...but then goes into the live usb and I can open a terminal, I type df to see what particions are available and I see sdb1 / cdrom but no sdba....I then type in fsck sdba1 and the system replies fsck from util-linux 2.34...

does it mean my HD is screwed?

---

### Post by yancek on 2021-01-17
The partition with the problem as shown in the image in your initial post is the / (root) filesystem partition, sda2.  The command df -h only displays mounted partitions so that's not a problem.  It isn't mounted and should not be mounted when you run fsck.

>  .I then type in fsck sdba1 

Hoping that's a typo here as it is:  sda2.  What you should run is:  sudo fsck /dev/sda2  If that results in problems, you must post the exact command you used and the exact output for someone to further help.

---

### Post by Paddy Landau on 2021-01-17
> **yancek said:**
> &#8230; sudo fsck /dev/sda2
I would amend that slightly for safety:
```
sudo fsck -CMf /dev/sda2
```
[FONT=courier new]-C[/FONT]: Show progress (optional, but nice to have).
[FONT=courier new]-M[/FONT]: Don't run the check when the partition is mounted (prevents certain types of errors).
[FONT=courier new]-f[/FONT]: Do a full check even if the system doesn't immediately find a problem.

If you can't log in normally, boot into Recovery Mode and add [FONT=courier new]/forcefsck[/FONT] to the required partition before rebooting. If you can't even do that, a Live disk is your only alternative.

---

### Post by abelito8 on 2021-01-17
wow, it seems that it worked! so complicated...so simple
thanks a lot

---

### Post by abelito8 on 2021-01-17
thanks a lot, I managed even without booting from live!

---

