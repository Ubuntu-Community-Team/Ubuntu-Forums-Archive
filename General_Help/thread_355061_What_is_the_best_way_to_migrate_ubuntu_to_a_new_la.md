---
title: "What is the best way to migrate ubuntu to a new laptop?"
date: 2007-02-06
forum: General Help
---

### Post by xbytes on 2007-02-06
Hi all,

Got settled in to ubuntu now with evolution mail and Firefox also customized the system preferences and packages, and now I'm getting a new laptop AFAIK it has a SATA disk it is a Core Duo system also ThinkPad T60 so I just wanted to know the recommended way of moving my stuff to the new box would be?

I wouldn't imagine I could just dd an image of this install on to my new laptop as the hardware will be very different, or will Ubuntu detect the new system as a live CD would? also I can connect the HDD from my current system to the new one through USB.

hmm maybe a redetect hardware option for booting ubuntu could work, in a similar way to the Linux Live CD's that would be cool you could just pull your HDD from one machine and put it in another and wouldn't have to start from scratch, maybe this has been done already :confused: 

-xBytes

---

### Post by dcstar on 2007-02-07
> **xbytes said:**
> Hi all,

Got settled in to ubuntu now with evolution mail and Firefox also customized the system preferences and packages, and now I'm getting a new laptop AFAIK it has a SATA disk it is a Core Duo system also ThinkPad T60 so I just wanted to know the recommended way of moving my stuff to the new box would be?

I wouldn't imagine I could just dd an image of this install on to my new laptop as the hardware will be very different, or will Ubuntu detect the new system as a live CD would? also I can connect the HDD from my current system to the new one through USB.

hmm maybe a redetect hardware option for booting ubuntu could work, in a similar way to the Linux Live CD's that would be cool you could just pull your HDD from one machine and put it in another and wouldn't have to start from scratch, maybe this has been done already :confused: 

-xBytes

Most of your data and personal configuration is in your home directory, so you may just want to copy all of that (including the hidden files!!!) into the same place on a fresh install.

You should also copy your APT cache files to save downloading updates again.

You can waste far more time trying to twist an existing setup to work with radically new hardware than doing a fresh install and copying your personal data.

---

### Post by housam on 2007-02-07
I also vote for a fresh install. save your time .

---

### Post by etank on 2007-02-07
If you want to do a backup of the files with gui then I would recommend either kdar (KDE app) or sbackup. They are both in the repos. I think that you can expost a list of installed apps from synaptic as well and then import them on the new machine.

---

### Post by yota on 2007-02-07
Hi,

linux is very flexible about relocation and I succesfully migrated installs in various ways like:

[LIST]
[*]dd
[*]tar
[*]netcat
[*]cp -a
[/LIST]

the laptop from which I'm writing is using an installation that went trough 2 totally different harware combinations before (both laptops too).
In fact I'm so satisfied that now I think that "clean" reinstall are just a windows's bad habit: with linux you install one time and you are set.

Mostly you can expect ubuntu to be very smart about detecting your new hardware, as you could expect from the live-cd, but some manual tweaks are absolutely needed to conclude a succesfull migration.

The key points are:
[LIST]
[*]reinstall grub on the new hard drive
[*]correct /boot/grub/menu.lst to point to correct device/partitions (if needed)
[*]correct /etc/fstab to reflect your new partiotion layout (if needed)
[*]correct /etc/iftab to point to your new network adapter
[*]put needed modules in /etc/modules and remove ol ones
[/LIST]

As bottom line I can suggest to take the trip only if any of the above operation is fairly clear to you; if previous knowledge about is at hand, the whole process can be accomplished very quickly. Otherwise it can turn in a time consuming nightmare, maybe not worth the effort.

Hope it helps!

---

### Post by xbytes on 2007-02-07
Thanks for the pointers... I would actually like to try copying my install, as this would teach me something new rather than just going through the same setup process as I have already been through a few times, as I'm not that advanced in the terminal yet I'll probably have a n00b crisis or two but its all fun, anyway cheers for your very helpful re's

-xbytes

p.s. the ubuntu forums are great, thanks guys!

---

