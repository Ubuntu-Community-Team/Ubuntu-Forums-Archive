---
title: "Vesa and persistent (USB) not working together"
date: 2007-11-24
forum: General Help
---

### Post by nibl on 2007-11-24
This issue concerns Ubuntu on a USB drive.

On some laptops you need to start Ubuntu in safe graphics mode (kernel append command "xforcevesa"). On Gutsy this works fine in live mode, but not in persistent mode. The display only shows the splash screen for a while then it remains black. I have tried other options like vga=771 with persistent mode, but no difference. It seems like display options are not being recognised in persistent mode, only in live mode. Yes, the USB stick has a casper-rw partition. I followed the exact instructions.

I am aware of the thread about persistent mode. It does not mention display issues and it concerned feisty, gutsy has supposedly fixed persistent mode.

Here is the standard command from syslinux.cfg for live mode, which does work:

LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz quiet splash --

If you add persistent, the display no longer works properly:

append  file=/preseed/ubuntu.seed boot=casper persistent xforcevesa initrd=initrd.gz quiet splash --

The whole point of using a USB stick is to use persistent mode, so this problem is practically a show stopper because you cannot save data.


Does anybody have any ideas on what might help to get persistent mode working with alternate display modes?

Many Thanks.

Gutsy on 1GB USB stick, Amilo Pro Laptop.

---

### Post by rrsodl on 2008-01-30
I know this reply would come very late but it might come handy for some people.

I have a PC with a Ati Radeon graphics card, I bought it as Radeon 9250, Xp sees it as a Radeon 9250 but ubunto sees it as a Ati Radeon 9200 Pro and the driver ubuntu is using does not work with my card.

I found that in the safe graphics mode the graphics card worked ok but I could not save any changes so, I edited the file /media/ubunto710/sylinux.cfg and added to the persistent option the parameter xforcevesa. In other words forcing the permanet option to use the default vesa graphics driver.

Also, I configured the xserver ... sudo dpkg-reconfigure xserver-xorg and I opted for Vesa graphics card, Generic type, etc

After that, the problems I encountered were the well know .dmrc and .ICEauthority, both to do with permissions - plenty of info on how to solve that in this forum.

Rick

---

