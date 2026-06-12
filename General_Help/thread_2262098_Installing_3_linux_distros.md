---
title: "Installing 3 linux distros"
date: 2015-01-22
forum: General Help
---

### Post by Cyber72 on 2015-01-22
I've tried to check this out but found conflicting advice.

[COLOR=#0000cd]**Current state**[/COLOR]: laptop was XP I installed 12.04, 32 bit from a CD as the sole OS (ie never had dual boot). Updated to 14.04, 32 bit.

[COLOR=#0000cd]**Plan**[/COLOR]: i) to install 14:04, 64 bit as second OS (recently upped RAM to 4gb)
.........ii) to install a another distro (keeping both 14.04s because I want to keep the 32 bit version as a back-up until the other distro is up and running)
........iii) to replace 32 bit 14:04 with a third OS

[COLOR=#008000]**Questions**[/COLOR]
1 Is there anything I need to check about the 32 bit installation before I proceed? I read something about the grub but I didn't understand it.
2 Should I do all the partitioning before I install the 64 bit 14.04 or  not? If the answer is yes please recommend software for this.
3 Should I install 14.04 directlly from the net or download it to a usb fash driive and install from there?
4 When it comes to replacing the 32 bit 14.04 with a third OS do I need to do something in the grub first?
5 Is there anything else I need to know?

Thanks

---

### Post by Dreamer Fithp Apprentice on 2015-01-23
> **Cyber72 said:**
> 1 Is there anything I need to check about the 32 bit installation before I proceed?About the present installation? No. About the computer? Yes. Make sure it IS 64 bit capable, and make sure you have sufficient hard drive space for your plans.

> **Cyber72 said:**
> 
2 Should I do all the partitioning before I install the 64 bit 14.04 or  not?I would. Easier that way.

> **Cyber72 said:**
> 
 If the answer is yes please recommend software for this.gparted

> **Cyber72 said:**
> 
3 Should I install 14.04 directlly from the net or download it to a usb fash driive and install from there?I've never done a pure from-the-network installation though I suppose it is possible. Heck, you can actually boot from a network, so sure it's possible. But if anyone has set it up to make it easy to do that, I don't recall reading about it. Which doesn't mean it isn't out there - may just mean I'm not up to date or never noticed it. There are mini.iso images for Ubuntu and Debian you can burn to a thumb or a cd and install from. That's how I usually do it now. When you do it that way the image is only a few 10s of megabytes and when you boot from it you pick software you want in a kind of multiple choice menu and download the current versions only, so when you finish, you are already up to date. It is a lot faster than downloading, burning, installing from a regular live/installer cd or thumb, and then rebooting and updating. And you install exactly what you want - like ordering a la carte. It is a little less user friendly, and you can accidentally install a system that won't do much of anything if you don't pay attention or think about what you are doing. It offers more choices, including the choice to screw it up your own way. Using the regular installers makes a lot of reasonable and workable choices for you. And you can change anything you don't like later. Less chance to screw up. And, as a nifty bonus, you have a live disk left over when you finish. They can come in handy. Your call.

> **Cyber72 said:**
> 
4 When it comes to replacing the 32 bit 14.04 with a third OS do I need to do something in the grub first?No.

> **Cyber72 said:**
> 
5 Is there anything else I need to know?If you are human and under 200 years of age, probably a lot. But I think that about covers the immediate objective. I'm assuming you have already read enough about multibooting to have some idea of how you want to partition the drive. If not, there are lots of threads here discussing that.

Oh, and of course: BACK UP YOUR DATA FIRST, as always.
For that matter if you value the settings and tweaks you've made to your present system, you could back that up with something like fsarchiver (which I really like), but if you plan to wipe it out anyway, I guess there isn't much point.

---

### Post by sudodus on 2015-01-23
Good advice by* Dreamer Fithp Apprentice *:-)

I can add that it is worthwhile to [try a few flavours: Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by Cyber72 on 2015-01-23
Thanks for your time Dreamer and such a sraight forward reply.
I will take your tip sudodus thanks.

I will give the thread 48 hours before I mark as solved in case anyone has something to add. Although I think I know what I need to do now.

---

### Post by Impavidus on 2015-01-23
Typically, the last system you install takes control of grub. That system will be the default in the grub menu and you'll have to run **update-grub** from that system to get kernel upgrades in any of your systems working. A system can take back control of grub by reinstalling it from that system.

---

### Post by fantab on 2015-01-23
> **Impavidus said:**
> Typically, the last system you install takes control of grub. That system will be the default in the grub menu and you'll have to run **update-grub** from that system to get kernel upgrades in any of your systems working. A system can take back control of grub by reinstalling it from that system.

+1
Grub can only be tweaked from the distro which installed it.
I multiboot and having a custom grub menu helps: [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

Because I multiboot I don't use a separate /home paritiion, it would get messy. Instead I use a common/shared, simple ext4 partition to store my DATA. 'Home' is in '/' with distro's own settings.
Later I would mount the partition with 'fstab'.
So I have about 4 20gb partitions with different distros' '/' and one 900gb ext4 partition for my DATA. Also one swap partition on a HDD is enough and will be shared between all distros.

---

### Post by verymadpip on 2015-01-23
Hi everyone.
Regarding the grub thing:
Is it possible to choose a distro to control booting & install grub belonging to the other distros in their respective partitions?
For the sake of argument let's say one wanted Ubuntu 14.04 LTS to control the boot process for itself &, say, 14.10 & 15.04.

Although I suppose with the "interim" releases it would be simpler for one of them to control booting as they'll need to be replaced before than the LTS...

Sorry, I don't mean to muddy the waters, just looking at options.

---

### Post by sudodus on 2015-01-23
> **verymadpip said:**
> Hi everyone.
Regarding the grub thing:
[COLOR=#0000cd]Is it possible to choose a distro to control booting & install grub belonging to the other distros in their respective partitions?[/COLOR]
For the sake of argument let's say one wanted Ubuntu 14.04 LTS to control the boot process for itself &, say, 14.10 & 15.04.
...

> **Impavidus said:**
> Typically, the last system you install takes control of grub. That system will be the default in the grub menu and you'll have to run **update-grub** from that system to get kernel upgrades in any of your systems working. **[COLOR=#0000cd]A system can take back control of grub by reinstalling it from that system.[/COLOR]**

Yes, as described by *Impavidus*.

See this link [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by oldfred on 2015-01-23
I like to keep track of which install is where.
If you have mulitple drives and/or multiple installs worthwhile to run Boot-Repairs Summary report or the bootinfoscript which is really the first part of the Summary report.

       [URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info
[/URL]
 Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

[URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by Cyber72 on 2015-01-24
Many thanks

---

