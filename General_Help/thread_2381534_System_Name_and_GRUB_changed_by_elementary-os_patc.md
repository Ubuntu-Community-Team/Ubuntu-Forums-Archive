---
title: "System Name and GRUB changed by elementary-os patch"
date: 2018-01-02
forum: General Help
---

### Post by bhooshan-aj on 2018-01-02
Using Ubuntu GNOME 16.04 LTS 64-bit

I was recently trying to install Bookworm ebook reader ([github bookworm]("https://babluboy.github.io/bookworm/")) on this system and kept giving unmet dependencies error. Searched around and found that installed [COLOR=#6A6A6A][FONT=arial]**elementary-OS patch (**[/FONT][/COLOR][COLOR=#006621][FONT=arial]https://launchpad.net/~elementary-os/+archive/ubuntu/os-patches) solves the problem of [/FONT][/COLOR][COLOR=#333333][FONT=Menlo]**libgranite3, **I think. So I did it. I installed it. It changed some things. One of which is the "Base system" string.

[/FONT][/COLOR][IMG]https://preview.ibb.co/m3yfXG/Screenshot_from_2018_01_02_12_41_03.png[/IMG]

This has caused some changes in the GRUB boot menu as well. And I don't know what else.
I think most of the changes are just aesthetic. But I don't know. I'd like to revert back to the original Ubuntu..err...things. Any ideas?

---

### Post by col48 on 2018-01-02
Safest would be to restore from backup - otherwise there is the risk of the unknown biting back.

---

### Post by Cavsfan on 2018-01-03
You could customize the grub pretty easily.

The wiki in my signature explains how to do so and it's pretty straight forward.

Fairly sure the Base System line is just some text some where that can be edited.

---

### Post by bhooshan-aj on 2018-01-09
Exactly. I have been trying to find the place where it's saved. But have had no luck. I get results on how to change hostname instead.
I have already changed my grub etc. What remains is just a little annoying message that always appears saying "Welcome to elementary OS Loki" during boot due to these patches. 

EDIT---
I found the solution somewhere... For anyone who has the same problem.

> [COLOR=#111111][FONT=Ubuntu]The PPAs you used to install elementary not only provided elementary specific packages, but also *patched* many standard Ubuntu packages and with your apt-get dist-upgrade command they all get installed and mixed into your system. Which means some of the core packages are not from Ubuntu repository, but from those elementary PPAs.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]For example, This ppa [https://launchpad.net/~elementary-os/+archive/ubuntu/os-patches](https://launchpad.net/~elementary-os/+archive/ubuntu/os-patches)provides many packages that are also available in Ubuntu repository. Since the PPA provides those package with higher version (and patched of course), those are preferred by apt and get installed into your system while you did the dist-upgrade command.[/FONT][/COLOR]
[HR][/HR][COLOR=#111111][FONT=Ubuntu]For your specific problem, I identified the package which is responsible for showing the distribution name on top-left corner of Unity Panel. It is called base-files. I tested the elementary PPA by installing it and not surprisingly I too got those elementary marks :D.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]But to solve this, you just can't remove it, because this is an essential package and Ubuntu needs it. What you need to do is re-installing from Ubuntu repository. Use this command to do so.[/FONT][/COLOR]
sudo apt-get --reinstall install base-files/xenial-updates
[COLOR=#111111][FONT=Ubuntu]This command will install the package from Ubuntu's xenial-updates archive. After a logout and login, you'll see the changes reverted back.[/FONT][/COLOR]
[HR][/HR][COLOR=#111111][FONT=Ubuntu]To completely remove Elementary effect from your system, you should go back to Ubuntu versions for all packages. To do so, use ppa-purge (and not apt-add-repository --removecommand, which will just remove the repository entry). For example,[/FONT][/COLOR]
sudo ppa-purge ppa:elementary-os/daily 
sudo ppa-purge ppa:elementary-os/os-patches
sudo ppa-purge ppa:elementary-os/testing 
sudo ppa-purge ppa:mpstark/elementary-tweaks-daily
[COLOR=#111111][FONT=Ubuntu]ppa-purge will remove packages from these PPAs and install the ones from Ubuntu archives.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]**Note:** If you already removed the Elementary PPA entries (by deleting the lines from sources.list files) add them again and then use ppa-purge.

Credits to Anwar.[/FONT][/COLOR]


Not sure if I can post links of other website yet.

---

