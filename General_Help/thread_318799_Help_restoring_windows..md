---
title: "Help restoring windows."
date: 2006-12-14
forum: General Help
---

### Post by ftw_59 on 2006-12-14
So the other day I installed kubuntu for the first time and I liked it. The only problem was that my partitions weren't the size I wanted them and when I tried fixing them there was something on my harddrive that I couldn't fix therefore I couldn't change the partitions easily. So I figure since I had anything backed up already it would be easier just to start over from scratch so I threw in the system restore dvd. I get through the reformat then installation fine and when it asked me to reboot I get greeted with the grub screen which gives me only an error. ****. So installed kubuntu giving it the entire HD to work with. The only problem now is that a lot of my data I need is on dvd-rws, that won't read in kubuntu. I want to get back to a dual boot having most of the HD for kubuntu but I can't get windows to install properly. I found this but I can't get past the first set of code because I'm new to this and don't know how to do it x_X
> How to get rid of GRUB when removing a Linux distribution
 A few days ago, I tried restoring my laptop to its original factory state by running the recovery CDs that it came shipped with. This mostly worked fine, but after the recovery Windows wouldn't boot properly, and the laptop would freeze with only the word GRUB on its screen. 
 A few people are going to say "Well, install Ubuntu then", but that's not the point here. The point is restoring the system properly, so it can boot Windows again. I agree that this is actually a bug in the recovery software, but the same thing happens when you delete your Linux partitions and re-grow your Windows partition (which is what some people want, after trying a distribution for a while). 
 First, you have to get the system to boot Windows. To do this, you need a bootable CD image with GRUB on it. It can be a tiny CD image, with only GRUB on it (probably the smallest CD you'll ever burn :))
 You can create one like this: 
$ mkdir -p iso/boot/grub
$ cp /usr/lib/grub/i386-pc/stage2_eltorito iso/boot/grub
$ mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso
 When you boot that CD, GRUB will start up and give you its shell. From this shell you can start Windows like this (change '(hd0,0)' to something else if your Windows installation isn't on /dev/hda1, see the GRUB manual for more on that): 
> root (hd0,0)
> chainloader +1
> boot
 Windows should now start. It might ask you to complete some steps of the OEM installation (entering your time zone and username, for example), and then reboot. Just re-enter the GRUB stuff to re-start Windows. 
 Once Windows is done starting, you have to find the I386 installation directory, either on the installation CD, or on C:\I386 as it was on my laptop, and install the Recovery Console by running C:\I386\WINNT32.EXE /cmdcons. 
 After doing this, you should reboot the system again (using the GRUB trick) and choose the Recovery Console option from the menu that appears. You will get a very limited shell, where you can type 'fixmbr' to fix the MBR on your boot drive, clearing the GRUB bit and allowing you to start the sytem. To do so, remove the GRUB CD from your drive, and type EXIT at the console. 
 You should now have a properly booting Windows system, without a hanging piece of GRUB.

Someone help please ;-;

---

