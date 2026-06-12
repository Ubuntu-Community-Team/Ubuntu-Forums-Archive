---
title: "Boot stuck in infinite loop"
date: 2013-08-03
forum: General Help
---

### Post by ruberad on 2013-08-03
I've researched and seen a lot of other infinite boot loop questions, and they all seem to boil down to reinstalling grub with the boot fixer utility. But I'm not sure whether my problem falls in that category, since I think I'm in a state after grub turns over to the ubuntu boot sequence.

What I'm seeing is it gets past the bios and all that, and I get to the black screen where ascii boot messages appear before the Ubuntu splashscreen with the dots. I see only two lines:

Could not write bytes: broken pipe
Checking battery status                       [OK]

Then it flashes all black, and back to those two lines, ad infinitum.

If I hit the button to power down, I get the splash screen where the dots turn off, and it shuts down.

So my question at this point is, is this a grub problem that would (could?) be fixed with the boot utility, or is it something else? 

FYI I am running 12.04, I reinstalled it about a month ago after getting a replacement, refurbished 64GB SSD under warranty from Crucial. After install, I immediately enabled trim. I've got like a 20G partition on the SSD for boot and OS, some for swap, rest for /home, and a separate spinning disk mounted to /data.

Single-boot only, no windoze. 

Before the problem occurred, an update had some failed packages. Also I tried to manually apt-get install lame, and that failed too, which is why I decided to reboot in the first place.

In the meantime, I've been running all week off a live CD with Try Ubuntu.

---

### Post by carl4926 on 2013-08-03
I would chroot with the Ubuntu live CD/USB whatever you used. And check your system from there.
Usually if grub is faulty there will be a message

---

### Post by ruberad on 2013-08-03
Thx, chroot is a new one on me. But I don't really know what I should be checking or what to look for. 

What are the signs that I should just give up and reinstall 12.04 again?

---

### Post by zteam2 on 2013-08-03
What happens if you just try booting up with another kernel?

Hold down the shift key, after your computer shows , your BIOS logo and select a older kernel and see if it boots up there, if not the first thing I would do is booting of a live-CD / live-usb and run a filesystem check with fsck.

---

