---
title: "grub is not editable"
date: 2023-04-03
forum: General Help
---

### Post by rsdix on 2023-04-03
I replaced the motherboard and processor. Ubuntu booted up and worked fine, but rebooted on shutdown. I mistakenly thought the problem was Grub. I started the Grub Customizer. Didn't save anything and just closed it. Reboot problem I solved in Bios. But instead of a beautiful Grub bootloader, I got 4 line menus: 1 Ubuntu, 2 Windows and two test memory menus with black background. There is no default boot timer. The /etc/default/grub looks correct GRUB_TIMEOUT="5". But update-grub doesn't change anything. Grub Customizer doesn't change anything either. Grub Customizer with theme but I have just regular black background. My guess is that update-grub is using some other files or is generating in the wrong place. I would like to get downloads with a theme, or at least get a download timer.

---

### Post by ajgreeny on 2023-04-03
Much more detail is needed so please show us the full content of your /***etc/default/grub*** file using code tags (see my signature below for a how-to).

Also I suggest you avoid using grub-customizer as it can create more difficulties than it solves by replacing some of the default configuration files for grub with its own versions.  If you have used it previously that could already be adding to the confusion.

---

### Post by rsdix on 2023-04-03
> **ajgreeny said:**
> Much more detail is needed so please show us the full content of your /***etc/default/grub*** file using code tags (see my signature below for a how-to).

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Ubuntu"
GRUB_TIMEOUT_STYLE="menu"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

GRUB_BACKGROUND="/home/dmitrii/grub_back.png"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_DISABLE_OS_PROBER="false"

GRUB_THEME="/boot/grub/themes/GRUB2-DarkSquares/theme.txt"
GRUB_SAVEDEFAULT="false"
export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="magenta/black"

---

### Post by rsdix on 2023-04-03
2 hard drives installed. SSD with Ubuntu and HDD with Windows 10. In bios boot SSD first, HDD second. But in Ubuntu HDD - sda, SSD- sdb.

---

### Post by ajgreeny on 2023-04-03
Try adding the line
**GRUB_HIDDEN_TIMEOUT_QUIET=false**
tom your /etc/default/grub file then run ***sudo update-grub*** to see if that makes the timeout count down.

There are many good web pages available with helpful details about grub and how to change how it's displayed so have a good look at
[https://ubuntuforums.org/showthread.php?t=1195275](https://ubuntuforums.org/showthread.php?t=1195275)
and
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
 
I personally prefer the first of those two as it has much more detail, however, as grub shows only for a couple of seconds on my machines I'm not really bothered about making it look good, though I do want it to show by default so that I can change the kernel I boot to more simply than if grub is hidden.

---

### Post by rsdix on 2023-04-03
> **ajgreeny said:**
> Try adding the line
**GRUB_HIDDEN_TIMEOUT_QUIET=false**
tom your /etc/default/grub file then run ***sudo update-grub*** to see if that makes the timeout count down.

Doesn't change anything

---

### Post by tea for one on 2023-04-04
Is Grub Customizer still installed?
Have a read of this info in order to be aware of the changes made.
[https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)

If you wanted to add text colour and background to your Grub screen, there are less intrusive ways to do this.
However, if Grub Customizer is installed and working (even partially), then it is very difficult to offer reliable advice.

Would you be prepared to back up Ubuntu and start with a fresh installation?
Then, we can help with Grub background, text colour, boot timer etc.

With reference to the thread title, [COLOR="#0000FF"]grub is editable[/COLOR] with[COLOR="#0000FF"] sudo[/COLOR] privileges.

---

### Post by ajgreeny on 2023-04-04
It may help us a great deal if you run **Boot-Repair** as shown in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run any default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may make it a lot easier to figure out what's going on here as something does not make complete sense if the /etc/default/grub file you edited is not making any differences to what actually happens at boot.

---

### Post by rsdix on 2023-04-04
> **ajgreeny said:**
> It may help us a great deal if you run **Boot-Repair** 


[https://paste.ubuntu.com/p/kbH8GBhPGP/](https://paste.ubuntu.com/p/kbH8GBhPGP/)

---

### Post by rsdix on 2023-04-04
> **tea for one said:**
> Is Grub Customizer still installed?

yes

> **tea for one said:**
> Would you be prepared to back up Ubuntu and start with a fresh installation?


Not now, I want to try to solve it without reinstalling.

---

### Post by tea for one on 2023-04-05
Just a few comments after seeing the boot-repair report:-

In post 3, you supplied details from /etc/default/grub.
The details in lines 135 – 141 of the report are different – Blue text is from boot-repair.

GRUB_DEFAULT="Ubuntu" vs [COLOR="#0000FF"]"0"[/COLOR]
GRUB_TIMEOUT_STYLE="menu" vs [COLOR="#0000FF"]"hidden"[/COLOR]
GRUB_TIMEOUT="5" vs [COLOR="#0000FF"]"0"[/COLOR]
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/home/dmitrii/grub_back.png" vs [COLOR="#0000FF"]GRUB_THEME="/boot/grub/themes/GRUB2-DarkSquares/theme.txt"
[/COLOR]
In post 4, you mentioned that you also have a Windows 10 disk.
The info is missing from the report.
Is Windows 10 installed in UEFI mode?

Line 58/59 - The UEFI firmware is from 2013 and the PC should be UEFI compatible.
Is there a compelling reason for installing Ubuntu in Legacy mode?

Line167 - drwxr-xr-x 2 root root  4096 Apr  4 18:55 proxifiedScripts
I think that this is connected to Grub Customizer.
If you run the default-repair from boot-repair, I do not know what happens.

---

### Post by oldfred on 2023-04-05
Anything with proxy in the filename is from grub-customizer.
I believe it does backup the default grub files, so they can be restored.
But often easier just do do a total reinstall of grub, but that erases any changes you have made including /etc/defaults/grub. Which you may want to backup. 
You then may want to remove the backup folder that was created in /grub.d.

The advanced mode of Boot-Repair offers the choice for a full reinstall of grub.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by rsdix on 2023-04-05
Thanks **ajgreeny. **Boot-Repair fixed all issues.

---

