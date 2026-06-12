---
title: "trouble configuring grub"
date: 2020-07-24
forum: General Help
---

### Post by coley9225 on 2020-07-24
I'm having trouble configuring my grub menu. I have grub-customizer installed on lubuntu 18.04 and lubuntu 20.04. It seems to be doing as designed in 18.04, but on reboot the menu is the same before. It worked well in lubuntu 19.10, but after upgrading to 20.04, I have an issue. It seems to allow me to change the menu order, but when I save the new configuration, it completely freezes my computer. No keyboard, mouse, and I have to a hard shutdown and reboot. I've tried sudo apt remove --purge, and reinstalled, but I still have the same issue of computer locking up. I know I can made a couple of config changes by editing /etc/default/grub, but how do I change the menu order from terminal. While I'm becoming more  comfortable with the command line,I'm a fairly new linux convert, I would need a fairly detailed set of instructions. I am open to a different GUI app to accomplish my goal, but I would still like to learn the command line better, and what better way than to risk a non-bootable system...lol. And yes, I have full backups,off disk, just in case the process goes sideways. Thanks for any help or suggestions you may be able to offer.

---

### Post by Dennis N on 2020-07-24
In the Ubuntu grub menu you will have:

[B]Ubuntu
Advanced Options for Ubuntu
System Setup
[/B]
You are asking about the menu order - do you have a 2nd OS installed? What do you want your menu to look like? 
Your question is hard to answer without knowing more.

_Basic Concept:_

You can customize menu entries to be added to the default ones just by copying menu entries from **/boot/grub/grub.cfg** to the **/etc/grub.d/40_custom** file, editing as needed, saving, and lastly updating the grub menu with sudo update-grub. 

_Additional Comments:_

**40_custom** can be renamed to **06_custom** to put the custom ones at the top of the grub menu.
For flexibility, you can have multiple 40_custom files (with different prefix numbers). 'custom' can be changed to something else as well.
You can supress entries created by os_prober to reduce clutter in the menu.

---

### Post by oldfred on 2020-07-24
Your signature mentions 19.10.

Ubuntu 19.10 Eoan Ermine
EoL - July 17, 2020

So 19.10 will not get updates nor be updateable. 

I prefer to edit 40_custom than use grub customizer. Grub customizer replaces the grub files with its own versions with proxy in the name. I believe it has a back up of the original grub files, but better just to totally reinstall grub, not just update-grub. Any changes you then have made to 40_custom will be overwritten. I typically copy my 40_custom into /home so my normal backup of /home includes that file.

---

### Post by coley9225 on 2020-07-24
Thanks for the quick replies. My signature needs to be updated, I just haven't done it yet. My current set up has windows 10, lubuntu 18.04.4, lubuntu 20.04 and linux mint cinnamon 19.3. I've been told to drop 1 or the other of my lubuntus, but I really like 20.04, and keep 18.04 as a fallback. I use timeshift, and I can restore my 20.04 for 18.04 if need arises. And my 20.04 is upgrade from 19.10. That said, I've seen numerous articles and posts that recommend not editing grub files directly, but to edit /etc/default/grub instead. However, if I can get to where I want to be by editing the other files mentioned, I'll give it a go. Like I said in OP, if my system becomes unbootable, I have good, full backups, and worst case, I have a clone of my drive.The menu order I'm trying to get is:
lubuntu 20.04
linux mint 19.3
lubuntu 18.04
windows 10
system settings (for uefi access)
advanced option for OSs (no particular order.
I'll try the reinstall grub and edit the files you mentioned, and let you now how it goes.
Thanks

---

### Post by oldfred on 2020-07-24
If UEFI installs, you will only have one /EFI/ubuntu/grub.cfg which is just a 3 line configfile to the full grub.cfg in your install. But it will be to last installed system unless you totally reinstall grub and then that system will be the default.

And only editing the grub and/or 40_custom of the default system will make any difference.

Also if grub in any system you have booted, then does a major grub update, it will refresh the grub & become the new default.

With multiple installs, I prefer to turn off os-prober, so it does not find my other installs and then manually add the one's I want into 40_custom. I have multiple old installs and some are obsolete, but still have a grub entry to find. And I do not want those obsolete entries in my grub, but do have other entries to boot ISO or reboot system that I do want.

some examples, version now obsolete.
[https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&page=54&p=13787835#post13787835)

[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by pbear42 on 2020-07-24
> **coley9225 said:**
> I'll try the reinstall grub and edit the files you mentioned, and let you now how it goes.
Don't use GC myself, but in my observation, when ordinary reinstall of Grub doesn't work, it's because Customizer has removed the executable flags from the Grub scripts.  You can fix that manually, but it's easier and more reliable to use [purge-and-reinstall]("https://help.ubuntu.com/community/Grub2/Installing#Purging_.26_Reinstalling_GRUB_2").  So, first run [COLOR=#0000ff]sudo apt purge grub-common[/COLOR], then run [COLOR=#0000ff]sudo apt install grub-efi-amd64-signed[/COLOR] (assuming it's a UEFI system, if BIOS run *sudo apt install grub-pc*).  This assumes you can boot.  If this needs to be done from a live session, you would need chroot.  I can give you the form of command for that also, but the solution I just mentioned is much simpler.

Enough cooks already on the 40_custom solution.  I do something similar (a custom.cfg file) and recommend highly doing one or the other.

---

### Post by Dennis N on 2020-07-24
You forgot the Ubuntu entry. I included it below. It's for the Linux OS from which grub was last installed. I think all of your Linux use 'Ubuntu' as their menu name when installed. 

```
lubuntu 20.04
linux mint 19.3
lubuntu 18.04
windows 10
Ubuntu
Advanced options for Ubuntu
System settings

```

_Tip:_
Let's say that 'Ubuntu' above is from Lubuntu 20.04. To keep grub from being installed by an upgrade in the other Linux and disrupting your scheme, you hold back grub from being upgraded in those. Only Lubuntu 20.04 can upgrade the grub version.

---

### Post by coley9225 on 2020-07-26
I finally, after much trial and error, was able to get my grub menu laid out like I wanted. After editing the 40_custom file, I had to rename it 07_custom,make it executable, and make 40_custom non-executable. It took some time, but I got it done without a GUI tool. I greatly appreciate the helpful tips provided. I will mark this as solved. Thanks again for the help. You guys are the greatest, and I'm proud to be a member of the linux community.

---

