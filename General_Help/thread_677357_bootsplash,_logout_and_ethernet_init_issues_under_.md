---
title: "bootsplash, logout and ethernet init issues under Kubuntu"
date: 2008-01-24
forum: General Help
---

### Post by Zeroangel on 2008-01-24
My friend is using an (ATI/Sapphire) HD 2400PRO card, and we is using the TV-out to send the signal to the TV.

The OS displays everything fine, and we have even got compiz working with the binary ATI catalyst drivers, however the bootsplash is extremely buggy and will cause his TV to flash a random weird design and then it goes strictly to bluescreen and stays there.

I've worked around this problem by editing /boot/grub/menu.lst and omitted the 'splash' entry from the boot list. Problem is that there are more problems than that.

1) During startup, eth0 does not initialize and we get no network/internet access. Working around this by creating a desktop shortcut to 'kdesu ifup eth0', which starts the adapter.

2) Konqueror hard-locks the system when invoking autocomplete in the address bar (I will further test this by trying when Compiz is disabled). Which means that if I even use the address bar, than I can count on hitting the reset button on my PC.

3) There is no other features available from the logout menu, but 'log out'. This includes missing entries such as 'Turn Off', 'Restart', 'Switch User', etc.

4) Attempting to log-out or even restart the X-Server using ctrl_backspace will show the default login background and hard lock the system. Forcing me to hit the reset button.

Anyone have any ideas on how to fix these problems?

My memory is a bit dicey, but I think these are his specs:
Sapphire HD 2400PRO (ATI chipset) using TV-Out
ASUS MSM-VD2 (or something like that)
Intel E2140 (Core 2 Duo)
1GB PC3200 RAM

---

### Post by Zeroangel on 2008-01-25
*BUMP!*

Also I should add that the bootsplash issue was occurring on a vanilla install of Kubuntu (but wasnt present on the LiveCD), so to try and get SOME graphics, I booted into failsafe mode and updated all the packages using apt-get.

It later occurred to me to simply remove 'splash' from the boot options, then I noticed the other problems.

---

### Post by Zeroangel on 2008-01-29
Just thought i'd post a quick update on this since I managed to solve the problem using google and a whole lot of ingenuity.

1) **For the eth0 problem**, I created a simple shell script called **init-eth0** which is basically```
#! /usr/sh
ifup eth0
exit 0
```made it executable and placed it in my */etc/init.d/* folder. Then I symbolically linked it to my rcS.d folder```
sudo ln -s /etc/init.d/init-eth0 /etc/rcS.d/S92-eth0init
```Thereby auto-initializing the adapter during the boot process.

2) **For the konqueror hard-lock problem**, I simply used dolphin in the meantime. I like Konqueror more, but Dolphin does what I need it to do.

3) **For the Log Out issues**, I found that they were caused by the extremely buggy ATI Catalyst drivers (fglrx), one of the workarounds was to edit either the **gdm.conf** or **kdmrc** files to force X to restart when the user logged out. These solved the problems partially. Strangely enough, I got logout options back when I used **GDM** as my login manager

Some additional issues were caused by the fglrx drivers including the TTYs being inaccessable but I have made enough progress to give me a usable OS.

---

