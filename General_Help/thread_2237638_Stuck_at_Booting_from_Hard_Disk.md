---
title: "Stuck at Booting from Hard Disk"
date: 2014-08-03
forum: General Help
---

### Post by Eric_234234234 on 2014-08-03
I use chrubuntu on my Acer C720 which used to work flawlessly until i ran some ubuntu updates (Can't remember what it was, just clicked OK...i know ... i know ) 
Since the update it got stuck in the Bios at "Booting from Hard Disk..." So i reinstalled chrubuntu from scratch.

This time after i resized the partition (there was unused space from chromeOS i wanted to use again) it got stuck at "Booting from Hard Disk..." again.
So i thought it might be a problem with the bios and updated it and reinstalled chrubuntu. After resizing the partition it got stuck again.

Then i tried boot-repair from a live-usb. Recommended repair did not fix it, "Restore MBR" broke it even more (Now it is stuck at "Missing OS...")
Any help would be greatly appreciated.

I have no problem installing chrubuntu again, but i would rather know whats causing the problem and fix it, and most of all prevent it from happening again.
PS The first time the error occurd the partition was resized a week earlier, and no live-usb was inserted.

---

### Post by Luke_Bennett on 2014-10-05
Did you get anywhere with this? I have the exact same problem - my dual-booted C720 switched off without warning (it was low on battery admittedly) and now I keep getting the "Booting from Hard Disk..." message and the blinking cursor, and have likewise got nowhere with boot-repair. I haven't gone as far as you did with the MBR restore yet, from the sound of it I don't want to either!

I'm not exactly sure what kind of boot-repair settings I should be looking at - neither legacy nor EFI seems right, though from my (limited) understanding Chromebooks/CoreBoot do their own thing anyway. I've tried setting both sda12 (standard EFI partition) and sda7 (where my OS lives) as boot partitions in GParted but it hasn't helped.

Can anybody else offer any advice? If the original problem is still outstanding and my comment takes things off-track then please say and I'll create a new thread, I don't want to be a distraction.

---

### Post by ian66 on 2014-10-05
Sounds like your flags got reset when you lost power. Open up shell on ChromeOS side at the login and run

> sudo bash
> crossystem dev_boot_usb=1 dev_boot_legacy=1
> set_gbb_flags.sh 0×489

Edit: I misread your initial problem. Those flags are for default booting into Legacy, probably not for your issue. Do you have anything inserted in the USB or SD ports?

---

### Post by Luke_Bennett on 2014-10-08
> **ian66 said:**
> Sounds like your flags got reset when you lost power. Open up shell on ChromeOS side at the login and run

> sudo bash
> crossystem dev_boot_usb=1 dev_boot_legacy=1
> set_gbb_flags.sh 0×489

Edit: I misread your initial problem. Those flags are for default booting into Legacy, probably not for your issue. Do you have anything inserted in the USB or SD ports?

The flags are still fine, I can boot into legacy mode and run live CDs ok. It's definitely something to do with it not knowing what to boot once it gets into legacy mode.

Unfortunately in further messing around I've screwed up the ChromeOS partition too (note to self, ChromeOS will die if you make any partition changes, even if they don't touch the ChromeOS partitions) so it looks like my only way out of this is to take a backup of my data partition, do a full recovery and reinstall and then restore the data. It would be good to know more about this issue though if anybody has info to share, as this is the second time my dual boot setup has got hosed and it feels like I can't rule out having the same issue again at some point.

---

