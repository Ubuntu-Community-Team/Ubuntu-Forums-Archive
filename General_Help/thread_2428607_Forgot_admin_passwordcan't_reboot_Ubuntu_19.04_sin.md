---
title: "Forgot admin password/can't reboot Ubuntu 19.04 single OS"
date: 2019-10-06
forum: General Help
---

### Post by devil2pay on 2019-10-06
I forgot my password. I've looked up everything I could to reboot and/or change my password but nothing is working. My computer was running Windows 7 a few months ago, until I replaced it completely with Ubuntu 19.04, so this is my first time using the new OS other than just after the install. In any case, pressing SHIFT or ESC at any point after rebooting doesn't work. The Ubuntu "splash" screen never appears regardless of what I do. After the BIOS, while pressing/holding SHIFT or ESC, the screen goes black, and then a dark maroon with a black vertical strip on the left side of the screen. Then it goes black again for a few seconds until my desktop comes up. Any attempt to change my password in command line asks for my password. I feel I've exhausted every avenue except asking here. Other than reinstalling Ubuntu all over again, is there a way to change my password and/or get into Grub after rebooting given the problems I listed above? Thanks

---

### Post by CatKiller on 2019-10-06
I believe the correct procedure is to hold Shift from the appropriate point, or to spam Esc, and which one of those is the right one depends on whether you're using BIOS or UEFI. It's possible that your settings are such that the keyboard doesn't work at that point in the process, anyway: both Fast Boot and a lack of Legacy USB can mess that up.

If you can't summon the Grub menu to get the root terminal recovery option, you can always boot from the live USB and chroot from there to reset the password.

Since whatever's on there is unimportant enough that you've just never touched it for months, a reinstall takes about 15 minutes.

---

### Post by TheFu on 2019-10-06
I would boot from a "Try Ubuntu" flash drive (the same you used to install), then have the installer setup a chroot on the install. That will give you a root shell, where you can change any password you like.  If you do a web search for "chroot from install ubuntu", some detailed instructions should be found.  The command to change a password is "passwd"

This is more complicated if, LVM was selected or if whole drive encryption was selected.  With LVM involved, you'll need to use vgchange -ay to get the LVM VGs and LVs activated first.  For whole disk encryption, you'll need to know the LUKS container name and at least 1 of the possible 8 passphrases.  If you only set 1 passphrase, then there is only 1.  I always setup a very long, painful-to-type passphrase for emergency needs, in addition to the split password+cryptokey passphrase I normally use.

You've discovered 1 reason not to have logins without typing a password.

IMHO, someone new to Linux shouldn't be running a non-LTS release. The last LTS was 18.04.

I'm afraid many of these things are being the knowledge for someone with just a few months of Linux experience.  None of it is hard, but tiny, trivial, issues will be hard to solve for someone without a deeper understanding of the OS.  A really good set of instructions that is followed appropriately might be workable, but usually there are slight changes necessary for each of our systems.  We are all just a little different and so are our computer.

If you do need to reinstall the OS, making a backup of your HOME and a list of all the installed packages ( **dpkg --get-selections** ) will be massively helpful for after you install the replacement version.

---

### Post by devil2pay on 2019-10-08
Thanks CatKiller. I just created another bootable USB and started over. It "works" now, but of course I've run into another problem. I'll do some research before asking for help. Thanks for the assist on this one though.

---

### Post by devil2pay on 2019-10-08
Thanks for the assist TheFu, but I have already created a bootable USB and now have Ubuntu 19.04 reinstalled and running. However, I've ran into a new problem, to which I'll research for a solution before starting a new thread. I will, however, take your advice to heart when and if it becomes necessary for me to do this all again. Thanks again!

---

