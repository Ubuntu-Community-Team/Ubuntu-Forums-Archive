---
title: "GRUB2 BootLoader not showing up."
date: 2013-07-04
forum: General Help
---

### Post by sdggfn on 2013-07-04
[TABLE]
[TR]
[TD="class: votecell"]I previously had Ubuntu 12.04. Then I installed Windows on  another partition. Since then, the BootLoader did not start showing up  when booting, and Windows started up asking me to log in. Then I made a  bootable USB with Ubuntu 13.04 but when I booted from the pendrive, just  a blank screen came with a message SecureBoot not enabled which  disappeared as soon as it came. I searched ubuntu forums and found a  similar question. The answer was to edit some lines of  boot/grub/grub.cfg . Here is the link  -  [http://ubuntuforums.org/showthread.php?t=2081912](http://ubuntuforums.org/showthread.php?t=2081912) .

[/TD]
[TD="class: postcell"]After doing the edits suggested in the above link, the ubuntu  installation screen came. I chose to upgrade my 12.04 to 13.04 . After  the 13.04 was successfully installed I restarted but the Grub2  BootLoader did not show up and booted into Windows directly. Since then  always this has happened. I also verified that 13.04 has been installed  by selecting Try Ubuntu and checking the partition on which I installed  13.04. All the folders such as bin,boot,.... etc were present. Can  anyone please inform how can I bring back the GRUB2 BootLoader with  booting options into Windows 7 and Ubuntu 13.04 and I possible, set  Ubuntu as the default OS to boot after the time-out period ?
 My hardware specifications --
Lenevo Ideapad z570 with intel i5 ( 64 bit ) 
      
[/TD]
[/TR]
[/TABLE]

---

### Post by grahammechanical on 2013-07-04
Windows has overwriten the Grub boot menu. This happened because you installed Windows after installing Ubuntu. The upgrade to 13.04 should have re-written Grub back into the boot system. You could use Boot repair to get a better understanding of where the boot files are on that hard disk and what is necessary to repair it. Boot Repair may even fix things for you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

