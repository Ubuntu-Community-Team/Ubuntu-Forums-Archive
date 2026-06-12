---
title: "Installing on Samsung Ativ 500t"
date: 2016-02-07
forum: General Help
---

### Post by Zxoraz on 2016-02-07
Is there any known way to install a version of Ubuntu on the Samsung Ativ 500t?

I've been looking around for solutions for weeks now, seen some forum threads talking about **similar devices **but no solutions provided there helped me install Linux on mine.

_**The problem**_
The device won't boot into the installation (after specifically choosing the device to boot from).
Instead, it skips to booting Windows 8.

**Tool used to make bootable USB out of ISO files**: Rufus.
**Distros**: Ubuntu Desktop 15,14,12,11 x86 & x64, Kubuntu, Xubuntu, ElementaryOS.

[U][B]Attempted Solutions
[/B][/U]
Disabled 'Secure Boot' from the BIOS (there's no option to disable Fast Boot if you're wondering)

Placing a 'bootia32.efi' in the /efi/boot/ folder and followed this guide: [http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/](http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/)

This on it's own brought me to a "GRUB COMMAND LINE" allowing me to type, nothing more.

I then renamed the install folder to install.386 and copied the 'boot' folder from a Debian ISO, which lead me to see an Ubuntu menu,
After choosing an option (literally any option) it caused the device to freeze.

I also tried installing Debian, which also froze right after choosing an option. (I wasn't sure if it froze so I let it sit like that for around 4-5 hours)

___

I'd really appreciate any additional help that might put me on the right path!

---

### Post by oldfred on 2016-02-08
Most users have issues with the install of the 32bit UEFI.

You now are into what drivers it may need.

Are you installing Ubuntu or one of the flavors. Usually those Atom systems need a lighter weight version as full Ubuntu uses Unity which requires a newer system and newer better video system.
Often Lubuntu or Xubuntu work better.

These may be similar, even if different model.
       Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
[https://sturmflut.github.io/linux/ubuntu/2015/02/04/installing-ubuntu-on-baytrail-tablets-version-2/](https://sturmflut.github.io/linux/ubuntu/2015/02/04/installing-ubuntu-on-baytrail-tablets-version-2/)

More links
[http://ubuntuforums.org/showthread.php?t=2307022&page=2&p=13410393#post13410393](http://ubuntuforums.org/showthread.php?t=2307022&page=2&p=13410393#post13410393)

---

### Post by Zxoraz on 2016-02-08
I tried to install all of the distros mentioned in the thread, (Ubuntu, Xubuntu, Lubuntu, Kubuntu and more).
I'll try to follow those guides and report back..

**Another question about the 32bit UEFI:**
It seems like the other devices that people have had issues installing Linux on are actually 64 bit systems - while the Ativ 500t is said to be 32 bit, (not just 32bit UEFI)..
does that make any difference as to what I should do when attempting to install Linux on it?

---

### Post by oldfred on 2016-02-08
You probably need to look up specs on your specific Atom chip.
Most seemed to be 64 bit, but with 32 bit UEFI.
There are many threads on the various devices with Intel Bay Trail Atom chips and their issues.

If really 32bit, not sure how to convert 32 bit installer to UEFI. That may just be creating gpt partitions and adding an /boot/efi partition on installer with grub's 32 bit version.

older thread:
 Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)

---

### Post by gauthier3 on 2016-04-30
Hi,

I'm new here but also looking to install another OS (preferably Ubuntu) on the Samsung ATIV 500T.
So far I have learned the following: 
- only 32bit is supported, and thus you should try to install a 32bit image of Ubuntu supporting 32bit UEFI booting
- some claim that this tablet is 'hardware-locked' to windows. I have not found this to be true: I succeeded in installing and booting Remix OS (using this tool: [http://forum.xda-developers.com/remix/remix-os/rmxinstaller-x64-32bit-remixso-t3332239](http://forum.xda-developers.com/remix/remix-os/rmxinstaller-x64-32bit-remixso-t3332239)). However, every time I boot into Remix, I get stuck at the pulsating Remix OS. It is thus not really functioning, but I believe more experienced people could remedy this.
- Samsung support is non-existing, and Ubuntu development for tablet pc's is seriously lacking and/or disappointing.

Hope this post helped you and is not too much off-topic, if you ever manage to get Ubuntu running on the ativ 500T, please contact me!

---

