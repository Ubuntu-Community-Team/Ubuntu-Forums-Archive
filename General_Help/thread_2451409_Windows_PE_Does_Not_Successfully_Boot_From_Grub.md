---
title: "Windows PE Does Not Successfully Boot From Grub"
date: 2020-10-03
forum: General Help
---

### Post by cedric9 on 2020-10-03
To make a long story short, I have two - one terabyte Seagate Barracuda hard drives which I recent upgraded from my older Seagate Barracuda 500 drives.  

Kubuntu 20.04 is installed on sda1. I used to have Windows 8 installed on sdb1, but it developed too many registry problems, so I reformatted sdb1 as an empty NTFS partition and just used it for extra storage for the time being.  

Also, after I got rid of Windows 8, I started using Hiren's BootCD Windows 10 PE boot disk to defrag and to check fix any errors which may occur on my NTFS partition. Using Hiren's BootCD PE (actually HBCD_PE_x64) worked out well without any problems but it was a little bit inconvenient.  

The problem is that booting Windows PE from a bootable DVD seems to take around 3 - 5 minutes, while booting PE from a USB stick seems to take anywhere from 1.5 to 2 minutes.  After playing around a little bit I was able to get Windows PE too boot from my sdb1 partition, without having to boot it from a bootable DVD or bootable USB stick.  

The Windows PE on sdb1 shows up in Grub boot menu as "Windows Recovery Environment (on /dev/sdb1".  Problem is when I try to boot Windows PE from this option it fails, and instead I end up with a black and white screen "Stating none bootable disk, please insert floppy disk and hit enter."  (My machine doesn't even have a floppy drive. LOL.)

Also, if I got into my system bios and change the hard drive boot priority, then Windows PE on sdb1 will boot and run just fine.  Also, it seems to take less than 30 seconds to boot PE this way, which is why I'd like to get it working in the Grub boot menu.  

Not sure what other sort of information I should include other than I'm running my bios in legacy mode (until just recently I was using Kubuntu 18.04 32 bit).

Any info greatly appreciated.

(Specs below)
Operating System: Kubuntu 20.04
KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.4.0-47-generic
OS Type: 64-bit
Processors: 4 × Intel® Pentium® Gold G5400 CPU @ 3.70GHz
Memory: 7.6 GiB of RAM
Hard Drives:  Two 1 TB Seagate Barracuda

---

### Post by CelticWarrior on 2020-10-03
If you do not have Windows now, why did you format it as NTFS?

---

### Post by cedric9 on 2020-10-04
> **CelticWarrior said:**
> If you do not have Windows now, why did you format it as NTFS?

Because I plan on installing a new version of Windows in the future, and I still have a lot of MS Office type documents which I want to keep.  Also, I don't know very much about ext4 so wanted to be cautious before making too many changes at once.

---

### Post by oldfred on 2020-10-04
With regular Windows, grub only boots working Windows. So if hibernation or chkdsk needed grub will not boot it. 
But not sure how Hiren's is configured, but may be way grub is booting it.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by cedric9 on 2020-10-04
Edit the file /boot/grub/grub.cfg by entering the below command at the prompt.

sudo gedit /boot/grub/grub.cfg

Scroll down to the section titled:
### BEGIN /etc/grub.d/40_custom_proxy ###

Look for the line,"set root='(hd0,msdos1)'".

Add two empty spaces below the line referencing (msdos1) and add the below lines into the empty spaces you just created:

"[COLOR=#ff0000]ntldr /bootmgr[/COLOR]"
"[COLOR=#ff0000]boot[/COLOR]"

Save the changes in the gedit text editor,and close the file.  

I'm not sure if it is necessary to do so, but I invoked the "sudo update-grub" at this point.  



========= BELOW TEXT IS PARTIAL SAMPLE FROM - /boot/grub/grub.cfg ==========================================

### BEGIN /etc/grub.d/40_custom_proxy ###
menuentry "Windows Recovery Environment (on /dev/sdb1)" --class windows --class os $menuentry_id_option 'osprober-chain-79D7BB247ECCE0E2' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    [COLOR=#ff0000]ntldr /bootmgr
    boot[/COLOR]
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  79D7BB247ECCE0E2
    else
      search --no-floppy --fs-uuid --set=root 79D7BB247ECCE0E2
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/40_custom_proxy ###

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Making the above modifications to /boot/grub/grub.cfg gave me a working menu option which would boot Windows PE from sdb1, but in order to get the video to display correctly I had to make the below changes to my    
 /etc/default/grub file.  

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Modify /etc/default/grub by invoking the below command at the command prompt.

sudo gedit /etc/default/grub

Look for the line "# GRUB_GFXMODE="640x480"" and add an empty space below it.

add the below line below the already existing hashtaged out line referencing 640x480.
(I left the original line referencing 640x480 in place in case I wanted to go back to original settings.)

Add the below line into the empty space you just created below the 640x480 line.

[COLOR=#ff0000]"GRUB_GFXMODE="1024x768"[/COLOR]  

Save the changes in the gedit text editor,and close the file.  

Invoke the "sudo update-grub" at the command prompt in order to update grub.

========= BELOW TEXT IS PARTIAL SAMPLE FROM /etc/default/grub =========================================

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
# GRUB_GFXMODE="640x480"
[COLOR=#ff0000]GRUB_GFXMODE="1024x768"[/COLOR]
==============================================================================================

Making the above changes to "/boot/grub/grub.cfg" and "/etc/default/grub" gave me a grub boot menu option which successfully boots Windows PE from my sdb1 partition. Also, based my changes upon info I found at the below forums:

[https://forums.linuxmint.com/viewtopic.php?t=173945](https://forums.linuxmint.com/viewtopic.php?t=173945)
[https://askubuntu.com/questions/396720/grub2-is-it-possible-to-boot-in-window-8-by-directly-loading-the-bootmgr-withou](https://askubuntu.com/questions/396720/grub2-is-it-possible-to-boot-in-window-8-by-directly-loading-the-bootmgr-withou)

---

### Post by cedric9 on 2020-10-04
Also, here is how I actually got Windows PE onto my sdb1 partition in the first place.

1.  Used WoeUSB to burn Hiren's BootCD PE ISO to a 100 GB external USB hard drive.

2.  Verified that external hard drive was bootable by installing it into a laptop. (Booted no problem)

3.  Return 100 GB hard drive to USB enclosure.

4.  Connect USB external hard drive to desktop I want to run Win PE on, and booted desktop from Hiren's BootCD PE. DVD, not from external hard drive.

5.  Used Mercrium Reflect program in Win PE to make a back up image of the external USB hard drive.  (Stored the image in a mostly empty partition in my desktop.

6.  Shut down desktop, remove USB external hard drive. Reboot desktop from Hiren's BootCD PE. DVD, and used Mercrium Reflect program to restore image to sdb1 partition.

At this point I could only boot into PE on my sdb1 partition by changing the hard drive boot priority in my bios settings.  However, after I made the above changes to /boot/grub/grub.cfg and /etc/default/grub I'm now able to boot PE from the Grub menu.

---

### Post by cedric9 on 2020-10-08
I recently uncovered something new related to running Windows PE from a hard drive along side Linux, and I decided to update this post with one more piece of information in case someone else is trying to do something like this, and they happen to stumble across this via Google in the future.

To begin with, I noticed that if I rebooted my machine, then Windows PE would load correctly when selected from the Grub menu.  However, if I did a hard boot, such as first thing in the morning, then my monitor would continue to display the background image for my Grub menu as Windows PE is booting up.  Actually, the GUI for Windows would never load up on my monitor, and it would just display my boot menu background image, no matter how long I waited.

It appears that the fix is to enable the below line within the /etc/default/grub file, by removing its hashtag symbol.  

Before: 
# GRUB_TERMINAL="console"

After:  
GRUB_TERMINAL="console"

For whatever it is worth, I made the above change and now Windows PE loads correctly from my Grub menu after a hard boot, as well as after a reboot.

---

