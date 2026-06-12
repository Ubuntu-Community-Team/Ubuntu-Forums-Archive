---
title: "Ubuntu crashes when upgrading kernel via software updater"
date: 2015-06-20
forum: General Help
---

### Post by dfehling on 2015-06-20
Hi, I'm sorry if this is not the appropriate place, but I couldn't see how to submit a bug report as I don't know which package is causing the problems. I have a brand new laptop, an Asus N550JK with 14.04 installed on it. I always run the system updates when the notification pops up. Once a couple months ago there was a kernel update and the laptop just shut down and wouldn't boot because something had happened to grub. I was able to fix that problem and hadn't had another problem until today. Again, I started up the laptop and started the updates via the notification and then ubuntu crashed during the process. 

There's no pop-up or message of any kind. Grub was fine this time, but the system just hung at the loading screen, so I went in to the "safe boot" mode and tried a few options like check for errors and fix packages and everything worked after another reboot.

Could someone help me figure out what is going on or direct me to the appropriate place. I am not comfortable at all with the idea of ubuntu crashing with every kernel update.

Thank you in advance!

---

### Post by Bucky Ball on 2015-06-20
*Thread moved to **General Help**.*

Bit early for bug reporting. Have you looked to see if one already exists? Best to have a good sniff around before reporting bugs.

Please try this. Open a terminal and issue these commands one at a time, hitting return after each. These commands will NOT upgrade your release to a newer one.

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Report any and all error messages.

The most effective way to get support here is to provide as much information as you can about the problem and what you've tried to fix it. What did you do to fix this last time, if you remember? Some clues would be good. Whatever you did last time is probably related to what happened this time and that, at a guess, has to do with a kernel upgrade.

---

### Post by dfehling on 2015-06-20
Hi Bucky Ball,

I looked around the bugs as well as a general search and couldn't find the same issue. I could be using the wrong search terms, but I don't think I am.

I ran the given commands and had no error messages. 

Please let me know what other details you might need. I am pretty good at following instructions and looking around in linux, but this is beyond me.

My laptop is dual-booted with Windows 8.1 and Ubuntu 14.04. I have a SSD. Windows came preinstalled, then I put Ubuntu on top of it. When I boot, I always get a grub menu with the option to boot into Ubuntu, more Ubuntu options, boot into Windows, and change bios settings. 

Last time the update went awry, the computer simply booted to a screen with a grub rescue prompt. I followed the answer by Anwar Shah here: [http://askubuntu.com/questions/159846/tried-to-boot-ubuntu-but-the-grub-rescue-shows-up-instead](http://askubuntu.com/questions/159846/tried-to-boot-ubuntu-but-the-grub-rescue-shows-up-instead) and was able to boot, and haven't had any issues until today.

Today, I started up the laptop, accepted the update prompt and went about working online. Sometime during the next 5 minutes or so, the computer went to a black screen and then started up. I booted into the Recovery Mode and ran the fsck and dpkg commands. I tried to run networking, but the prompt froze. When I restarted, the computer booted.

I installed linux-crashdump, but unfortunately it seems to not play well with Windows 8.1 and uefi, so I had to remove it. Can you suggest a next step? I tried to look through log files, but nothing jumped out at me, though I wasn't quite sure what to look for.

---

### Post by dfehling on 2015-07-08
Hi,

I just have my computer crash again today after a kernel update. I clicked on 'more details' as the upgrade was being installed and saw that it was updating the grub list and discovering the kernels when it force rebooted. Would you be able to help me find out how to get more specific information on what exactly caused the crash? It seems to be something with grub adding kernels, but I really don't know where to find out more.

Thanks in advance.

---

