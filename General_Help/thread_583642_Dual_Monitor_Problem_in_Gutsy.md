---
title: "Dual Monitor Problem in Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by burningbed on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/155034](https://bugs.launchpad.net/ubuntu/+bug/155034) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				After upgrading from Feisty to Gutsy my dual monitor setup stopped working.
This bug might be related to:
[http://ubuntuforums.org/showthread.php?t=579861](http://ubuntuforums.org/showthread.php?t=579861)
[http://ubuntuforums.org/showthread.php?t=570231](http://ubuntuforums.org/showthread.php?t=570231)
However it seemed sufficiently different to warrant a separate post.

I'm using an HP Pavilion dv1000 laptop with the intel centrino graphics chipset (i810 driver) and I have an external Lenovo ThinkVision monitor hooked up. The attached xorg.conf worked in Feisty (and Edgy), but now in gutsy, it is no longer usable. The login screen displays fine (in both KDM and GDM) but when KDE or Gnome are loaded, I can only see the background image, but no desktop (however, the startup sound for KDE or Gnome plays as if it was successfully started). Keyboard shortcuts or right clicking with the mouse have no effect. I can load failsafe, start kwin from Konsole and drag windows around both screens as desired.

[B]EDIT:
I have solved all problems by simply uninstalling xserver-xgl. This bug is therefore misclassified. Even when deleting the xorg.conf file I had a lot of display issues when xserver-xgl was installed. The display was very slow to update and the fonts were rendered very badly. By running apt-get remove xserver-xgl all those problems disappeared and the above xorg.conf file works just as in Feisty. It seems that xserver-xgl got automatically installed during the gutsy update and that this caused the problem.
[/B]

---

### Post by ubergeeknz on 2007-10-23
This worked for me too: I am using an HP Compaq nx8220 notebook with ATI Radeon X300 graphics.

However, the 'screens and graphics' control panel still did not work, even on a freshly built (dpkg-reconfigure xserver-org) xorg.conf (plus enabling the restricted fglrx driver).  When I try to select the second screen as a secondary, and click 'test', my screens go blank, 5 seconds later I am back to one monitor and the screens and the applet closes (!?)

Still, my old dual monitor config from Feisty works.  I am just pissed off that I can't automatically switch between single and dual mode (for when I work away from my desk) and i have to still open a bloody shell and copy xorg.conf files around every time.

---

### Post by tminuszero on 2007-10-24
After two days, an embarrassing 40+ reboots, and untold edits to my xorg.conf file, removing xserver-xgl solved my problem. I was able to revert to my initial, working xorg.conf file from when I was using Feisty, restart X, and bingo, it worked. I'm also using an ATI  x300

---

### Post by SeanS on 2007-10-31
> **tminuszero said:**
> After two days, an embarrassing 40+ reboots, and untold edits to my xorg.conf file, removing xserver-xgl solved my problem. I was able to revert to my initial, working xorg.conf file from when I was using Feisty, restart X, and bingo, it worked. I'm also using an ATI  x300

YES!!! I'm in the same boat.

Radeon 9800 pro here. 

**sudo apt-get remove xserver-xgl**

I must admit that I was starting to regret the upgrade to Gutsy.. hopefully now it's smooth sailing from here!

---

### Post by jmw86069 on 2008-02-16
I just wanted to add that this solution fixed my problem immediately (just had to log off and back on from failsafe session.)

I traced this issue through numerous red herrings, video drivers, xorg.conf settings, boot options, etc etc etc. What a complete waste of time. Of all the numerous posts on this issue here at ubuntuforums, apparently all but one (this one) have no resolution.

Thank you for posting your fix! Meanwhile, I hope the [underpaid] Ubuntu team can resolve the issue in the future! :-)

Best regards,

James

---

