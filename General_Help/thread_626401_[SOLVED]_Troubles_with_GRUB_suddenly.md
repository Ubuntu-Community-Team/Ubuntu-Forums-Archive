---
title: "[SOLVED] Troubles with GRUB suddenly"
date: 2007-11-29
forum: General Help
---

### Post by matthewcraig on 2007-11-29
Hoping for help!  GRUB started acting up and preventing a boot.  Was working fine, and didn't make any changes other than security updates.  Booted earlier today, in fact. Suddenly GRUB stops at the booting 1.5 screen!  I event tried to re-install Ubuntu and reformat the /boot with a new install.... it still stops at that screen!  There is no error message.  Anyone have an idea what could be happening?  I am perplexed and typing from a LiveCD which is not great.  Thanks in advance.

---

### Post by meierfra on 2007-11-29
Try reinstalling Grub:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by matthewcraig on 2007-11-29
Thank you for your reply.  I tried a completely new installation, as I said in my original message.

[Edit: Sorry, I should add that it came up okay on install, but when I added the restricted drivers, GRUB conked out like before.  I do not think it is a bad disk because of this!]

---

### Post by matthewcraig on 2007-11-29
What's really weird is GRUB starts up Ubuntu correctly when I boot with a Windows Installation CDROM in the drive.  Self preservation mechanism?

---

### Post by wylfing on 2007-11-29
Although it appears to "stop booting," just relax and wait for a while. See if it eventually goes into its regular boot-up routine after about 2 or 3 minutes.

---

### Post by matthewcraig on 2007-12-01
I think I fixed the issue.  After trying a number of other things, I took a breather and realized that it had to be a hardware issue.  I went into my BIOS and remembered that I had turned on USB Legacy Support to try and get GRUB to recognize my USB keyboard.  I disabled that again, and I have been able to boot ever since.

This is another reminder to myself to purchase a computer from a vendor who supports Ubuntu out of the box.  I would spend so much less time stressing about hardware incompatibilities.

---

