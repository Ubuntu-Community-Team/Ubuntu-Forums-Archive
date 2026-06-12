---
title: "Lubuntu 20.04 not starting"
date: 2020-09-24
forum: General Help
---

### Post by rbscairns on 2020-09-24
My PC has Lubuntu 20.04 as its sole operating system. Since installing a couple of months ago, all has been working well. A few weeks ago the mouse cursor froze on me so I powered off the PC and rebooted. That appeared to fix the problem. Today the same thing happened, my mouse cursor froze. I again rebooted the system but Lubuntu would not start.

Now when I start my PC. all looks good with the Lubuntu logo displaying and the little white balls moving underneath. This continues for about 20 seconds then the screen goes blank (black) and stays that way. I did wait over 2 hours, but still nothing happened. My PC does not have a hard disc activity light so I do not know what is happening there.

I have a Lubuntu 20.04 live CD and can boot into that but not the installed Lubuntu 20.04 operating system. When I boot using the live CD, I can see all files on my SSD, including my Lubuntu files.

What can I do to get my PC to fully open the installed Lubuntu 20.04?

---

### Post by Impavidus on 2020-09-24
Can you access the grub menu? There are a few things you can try from there.
Try booting an older kernel. Maybe there's a problem with a new kernel which was coincidentally installed right when you had your mouse problem.
Try booting in recovery mode. You'll reach a menu where you can try a few options. I think there's an option to fix broken packages. It may help if you forced a reboot while the system was automatically installing upgrades. Or you can enable networking and drop to a root shell, so you can manually run the commands to install upgrades and configure packages. Or you can resume booting, which should bring you to the GUI in safe graphics mode.

My hunch is that your Lubuntu system boots fine, except that there's a graphics driver problem, so it fails to show anything on screen.

What graphics hardware do you use?

---

### Post by rbscairns on 2020-09-24
> **Impavidus said:**
> Can you access the grub menu? There are a few things you can try from there.
Try booting an older kernel. Maybe there's a problem with a new kernel which was coincidentally installed right when you had your mouse problem.
Try booting in recovery mode. You'll reach a menu where you can try a few options. I think there's an option to fix broken packages. It may help if you forced a reboot while the system was automatically installing upgrades. Or you can enable networking and drop to a root shell, so you can manually run the commands to install upgrades and configure packages. Or you can resume booting, which should bring you to the GUI in safe graphics mode.

My hunch is that your Lubuntu system boots fine, except that there's a graphics driver problem, so it fails to show anything on screen.

What graphics hardware do you use?
How can I access the grub menu?

[INDENT]I have tried booting with "Shift" held down, no good.
Tried booting while repeatedly pressing "Shift", no good.
Tried booting with "ESC" held down, no good.
Tried booting while repeatedly pressing "ESC", no good.[/INDENT]

How can I boot an older kernel? I have no idea.

How can I boot in recovery mode? I have no idea.

The PC has Intel® 9th Gen HD Graphics 500. I didn't think this could be a problem as the PC works well when booted using an Lubuntu 20.04 live CD.

I can get into the BIOS by holding down "Delete" while booting.

---

### Post by Impavidus on 2020-09-25
You should be able to get to the grub menu using one of those methods. It may take some tries. It's best to configure grub to show that menu always, so that you have no problem using it that one day you need it.

[Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) may help. It can give us some more information about your system if you create a boot info summary. We need it to piece together some commands that can unhide the grub menu. Actually, I think that Boot-Repairs default repair unhides the grub menu. Make sure your live disk has the same version of Ubuntu as your installed system.

Intel graphics just work, usually.

---

### Post by rbscairns on 2020-09-25
I am still unable to get to the grub menu. I tried 10 times with [ESC] pressed and about half the times it took me into BIOS and the other half the PC just went into the start of Lubuntu and then a blank screen. I tried 20 times with [Shift] pressed and at all times the PC just went into the start of Lubuntu and then a blank screen.

I will try to get Boot-Repair. That could take a couple of days as it is 880MB. My ISP here in the Philippines limits me to 800MB per day and with our bandwidth here it will take several hours to down load.

I will get back to this thread once (if) I can get Boot-Repair going.

---

### Post by Impavidus on 2020-09-26
You've got a Lubuntu live disk, right? You can install boot-repair from the PPA in a live session. No need for that big 800MB bootable Boot-Repair disk. The PPA version is more up-to-date anyway.

You can do this via a live disk without boot-repair. Have a look here: [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing). Change grub's configuration file so that it shows the menu for a few seconds. But without details, I can't give exact commands.

---

### Post by Yellow Pasque on 2020-09-26
Can you press Ctrl+Alt+F1 when Lubuntu boots to blank screen and get to a terminal?

---

### Post by rbscairns on 2020-10-10
I would like to thank all who have offered me assistance with this problem. After 5 days of trying full time, it just became too much form me. As my data backup was only 32 hours prior to my OS failing, I decided that I could not spend more time on this problem. It was more economical for me to just accept the small amount of lost work and reinstall Lubuntu 20.04 on my PC. I will now spend a couple of days to configure my newly installed OS and restore my data.

---

### Post by guiverc on 2020-10-10
Just for FYI only.

If you need to re-install the OS because of some problem, rather than a clean install (with format), you can use *Manual Partitioning* in Lubuntu (*Something-else* in Ubuntu) select your existing partition(s), and as long as you don't *format* them, it won't touch any user data (no restores should be necessary).

Depending on release, it will do the following

- take note of your installed software
- erase system directories
- install system
- add back your additional packages (*may not work with groovy; this feature is being removed in all Ubuntu's*)
- ask to reboot

Server applications (which often store *config* files in system directories) do have data that needs to be restored, but all desktop applications store data in user directories which isn't touched unless you selected format. All of this assumes you don't have format checked.

Sorry it's a bit late for you, but should you need to do it again, a re-install takes minutes and is a quick (dirty) fix should you need a system back operational. Backups should always be performed first (it's easy to miss/forget to uncheck the format checkbox!)

---

