---
title: "Changes to plymouth causes black splash screen."
date: 2015-08-20
forum: General Help
---

### Post by cyberswim on 2015-08-20
hello, I understand these plymouth questions have been asked numerous times.  But, despite having carried out the suggestions in several pages and posts, I still cannot seem to resolve this issue.
On both physical machines and now virtualbox systems, I have tried to modify and/or install new plymouth themes.  The goal is to eventually create some completely new ones myself.  But, for now, I'm just trying to make an install or modification work.
So, like I'd said, I have tried manually modifying a theme, then placing it in /lib/plymouth/themes and issuing the ```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
``` command in terminal.
On some of the systems, I've simply installed plymouth manager, installed a random plymouth theme, restarted the computer to find that it was then displaying the black screen instead, as well.  
Could anybody offer any suggestions as to what i may be missing or a possible new system property that may not be accounted for in these past posts/articles/tutorials?
Thanks!

---

### Post by Dennis N on 2015-08-20
From my own notes, these are the steps I used (using Solar as an example). You don't mention how you installed the theme, but it must be installed if you can configure!

```
Solar Theme Example

Preliminary: Copy or move Solar Theme folder into /lib/plymouth/themes folder. 

Method 1: Command Line

Install the theme (puts it into a named group of alternatives)

sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/solar/solar.plymouth 100 

select the theme:
sudo update-alternatives --config default.plymouth 

update initramfs:
sudo update-initramfs -u 

```

Method 2 is to use the alternatives configurator which you would have to install to use. Same result, however.

As to the black screen, this might help, but no guarantee it will solve your problem. It is supposed to get splash going sooner. It used to work well for me, but I haven't done this (or an alternate Plymouth theme) recently.

```
Use the terminal and change working directory to
/etc/initramfs-tools/conf.d

Create a new file named splash with nano
sudo nano splash

Place this line in the file:
FRAMEBUFFER=y

Save and exit nano

Update the initramfs
sudo update-initramfs -u

```

---

