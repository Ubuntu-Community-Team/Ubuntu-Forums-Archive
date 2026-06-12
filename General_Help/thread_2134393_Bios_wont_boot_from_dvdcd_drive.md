---
title: "Bios wont boot from dvd/cd drive"
date: 2013-04-11
forum: General Help
---

### Post by Trublet on 2013-04-11
I recently installed Ubuntu 12.10 on my TOSHIBA S855 notebook and after giving me problems with internet connection ([http://ubuntuforums.org/showthread.php?t=2134383](http://ubuntuforums.org/showthread.php?t=2134383)) i have decided to try a different linux distro. The problem is now that Ubuntu 12.10 will not boot any (tried a few) live cd's i put into the disk drive. I have changed the boot order in the bios to put the Dvd/cd drive first, still wont boot. They only live cd's that boot are the Ubuntu 12.04 and 12.10 ones. Any help would be greatly appreciated. Please be clear in your instructions im not computer savvy.

Thanks

---

### Post by nerdtron on 2013-04-11
Some questions for us to help you...
What particular distro are you trying to boot? What application did you used to burn the ISO to disk? Have you tried the disk on other computers?
If 12.04 and 12.10 boots fine from the DVD drive I don't think this is a problem of the OS, I think you may not have burned the disk correctly.

Anyway (not sure for you but I'll stil say it), you can also test another distro by creating a bootable USB flash drive using this utility [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

goodluck and keep us posted on your progress.

---

### Post by Trublet on 2013-04-11
Im currently running 12.04 on this laptop, i used Brasero to burn the Fuduntu live disk and the Ubuntu 12.10 64Bit disc used to install the 12.10 that computer is currently running. Im pretty sure its not because i burned them incorrectly though because even the Fedora, Knoppix, BSD i got out of a linux user magazine wouldn't boot. I even tried the windows 8 repair disc i made (previously had windows 8) and i get the press any key to boot message but as soon as i press a key it just loads to a black screen then restarts and repeats that cycle. I tried the booting from USB with unetbootin and got the following error message.

Boot failure:a proper digital signature was not found. One of the files on the selected boot device was rejected by the secure boot feature.

That message appeared on a couple of distros i tried with the usb and the rest i tried got skipped over like the cd drive. =/

Thanks for helping me figure this out =]

---

### Post by fuduntu on 2013-04-11
> **Trublet said:**
> Im currently running 12.04 on this laptop, i used Brasero to burn the Fuduntu live disk and the Ubuntu 12.10 64Bit disc used to install the 12.10 that computer is currently running. Im pretty sure its not because i burned them incorrectly though because even the Fedora, Knoppix, BSD i got out of a linux user magazine wouldn't boot. I even tried the windows 8 repair disc i made (previously had windows 8) and i get the press any key to boot message but as soon as i press a key it just loads to a black screen then restarts and repeats that cycle. I tried the booting from USB with unetbootin and got the following error message.

Boot failure:a proper digital signature was not found. One of the files on the selected boot device was rejected by the secure boot feature.

That message appeared on a couple of distros i tried with the usb and the rest i tried got skipped over like the cd drive. =/

Thanks for helping me figure this out =]

Go into your BIOS and disable SecureBoot.

---

### Post by Trublet on 2013-04-12
I was about to face palm if that was the entire reason nothing was working but it wasn't. It still won't load the discs i have tried so far besides the Ubuntu ones but that did solve booting from a USB. Thank you!

---

