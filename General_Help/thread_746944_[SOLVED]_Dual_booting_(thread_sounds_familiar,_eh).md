---
title: "[SOLVED] Dual booting (thread sounds familiar, eh?)"
date: 2008-04-06
forum: General Help
---

### Post by linuxbeatswin on 2008-04-06
After a horrible catastrophe involving electricity and water this afternoon, I had to get a "new" computer. My entire Gutsy O/S was wiped out- no chance of saving it at all. I loved that thing- so many hours spent tweaking it!

I have two hard drives (one is XP on 40 Gig of 160 Gig of space) other is 40 Gig (empty). 160 Gig is master, 40 Gig is slave. I want to install Gutsy on the slave to leave space on the master for other things. I made sure that the hard drives were clean, and installed XP successfully. Everything works- sound, etc. It's a 200 model Compaq that I believe is all factory- no tweaks.

I've read   [http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)   several times, and want to make sure of the steps. I am extremely tired, and need this dual-boot of Ubuntu and XP to go flawlessly. Since both O/S's have to work by Sunday at 12:00. I've done everything I know to do, and have searched as much as I can (2 hours). I'm wiped out and desperately need help.

Would anyone take their precious time to help someone dedicated to learning Ubuntu?

---

### Post by BaffledMollusc on 2008-04-06
That is an extremely old thread.

You definitely shouldn't have to muck around with configuring the menu.lst file by hand. The standard installation will sort out the dual booting and install grub for you.

I can't remember what the steps in the installer look like, but what you need to do is choose manual partitioning in the partitioning step. In the installer choose your 40GB drive and create an ext3 partition (about 38BG) and a swap partition (about 2GB). Set the mount point of the ext3 partition to be "/" (without the quotes). 

I think that's all you need to do. The installer should set up the grub bootloader with Windows and Ubuntu entries for you.

---

### Post by Walc on 2008-04-06
then set up booting parameters, depending what would u like to set up to run at first
and u r done with basics.
Tweaking is another issue here, its inevitable to spent hours on that ;)

---

### Post by BaffledMollusc on 2008-04-06
Fair point, but you don't *have* to play with grub boot parameters if you don't want to.

The default is on booting to list all the OSes you can boot into, wait a few seconds to see if the user selects a different one, and if not then go ahead and boot Ubuntu. I was just trying to point out that it's all pretty much automatic to set up a dual-boot system, and the original poster didn't need to stress about it or follow complicated guides.

---

### Post by linuxbeatswin on 2008-04-06
Folks-
Thank you so very much for your help on this topic which has been discussed to death, I'm sure. I really appreciate all of your help.
After getting the sleep I so desperately needed, I was successful in installing both O/S's (although I cringed while the XP install was going.) S'ok, though- it still runs behind a Fedora server. 

(Windows- you have been served!)

Thanks again to all of you- you don't know how truly grateful I am!!!!

:guitar:

---

