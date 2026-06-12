---
title: "ATI driver problems"
date: 2008-01-03
forum: General Help
---

### Post by jacmac101 on 2008-01-03
After using Feisty Fawn with ATI video card (Radeon 1650) installed with no problems, I decided to install Gutsy 7.10 version of Ubuntu.  I cleared my partition for a new install. installed 7.10, and upon reboot I was informed of updates.  Installed the updates and rebooted and was informed that a ATI driver update was available.  Installed the update, and rebooted to a black screen.  I then used the terminal interface to reset the graphics driver. Rebooted again and was back to using the vesa driver 800x600.  Then I read about Envy, downloaded and installed Envy. Ran the program, detected my monitor ( Dell 2005 digital), detected my video card, recognized 1280x768 as a viable resolution, ask for re-boot. Reboot found that the vesa driver was active, and no recognition of the ATI driver from Envy. Ran Envy again and removed the ATI driver. After reboot I ran Envy again, and used the manual install to try an earlier driver, set up my configuration again, rebooted and now my DVD monitor is not recognized so I can't even reset the driver back to Vesa driver.  Any suggestions would be helpful.

---

### Post by RC Howe on 2008-01-03
If you have access to the recovery console (or a console in general), you may try running:
```
# dpkg --reconfigure xserver-xorg
```
Be warned, this will reconfigure your XServer, so you may want to not write any files besides monitor configuration and make a backup of xorg.conf. Somewhere along the way in the configuration process it will ask you to select a driver, choose VESA or perhaps FGLRX (the ATI driver for FireGL and Radeon cards).

It seems to me that your original problem was Envy installed the ATI driver, but you were still using the VESA driver in xorg.conf. If you decide to reinstall the ATI driver, pay a visit to System > Administration > Monitors and Displays, where you can choose your driver (Backup xorg.conf again).

---

### Post by Casual Fan on 2008-01-03
Don't run Gutsy, :(

BTW, if you want to be able to suspend or hibernate AND use your ATI card, you'll need to run Feisty.*

*probably. YMMV.

---

### Post by Rocket2DMn on 2008-01-04
Gutsy works fine with the open source ati driver, and you can sleep and hibernate.  Run the following:
get to a terminal (tty, like CTRL+ALT+F2), stop gnome, run the reconifguration, and restart gnome.
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```
You will be asked questions about your hardware - do your best to answer and when you get to the resolutions part, use TAB to move and SPACEBAR to select your monitor's max resolution and everything less.  Try the "ati" driver (open source), not "radeon" (proprietary).

---

### Post by Casual Fan on 2008-01-04
> **Rocket2DMn said:**
> Gutsy works fine with the open source ati driver, and you can sleep and hibernate.  Run the following:
get to a terminal (tty, like CTRL+ALT+F2), stop gnome, run the reconifguration, and restart gnome.
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```
You will be asked questions about your hardware - do your best to answer and when you get to the resolutions part, use TAB to move and SPACEBAR to select your monitor's max resolution and everything less.  Try the "ati" driver (open source), not "radeon" (proprietary).

Radeon is open source, Fglrx (or now Catalyst) is proprietary. And no Compiz without the proprietary driver.

---

### Post by Rocket2DMn on 2008-01-04
> **Casual Fan said:**
> Radeon is open source, Fglrx (or now Catalyst) is proprietary. And no Compiz without the proprietary driver.

Blah, my bad, I knew that.  But you can use Compiz with the open source driver.  Works fine for me, just might depend on the video card (I have a Mobility Radeon 9000).

---

### Post by jacmac101 on 2008-01-04
Thanks for all the suggestions but I have no access to run any commands with a black screen.  I know how to repair the driver problem from the graphic boot command prompt, but when I boot now the monitor does not give me the option screen to choose the boot. The monitor presents me with a message that it not recognized.  Guess I will go back to Feisty Fawn.
Thanks for the help.

---

### Post by Rocket2DMn on 2008-01-04
The black screen is because X is not configured correctly - you can still access a TTY (a terminal) by hitting CTRL+ALT+F1 (all the way to F6 if you want).  From there you can login and run the commands above which will allow you to configure X correctly.

---

### Post by jacmac101 on 2008-01-14
Thanks for all the help.  I did get into the command console, and re-set the graphics to the ATI driver. Reboot and the driver works now. All is well!

---

