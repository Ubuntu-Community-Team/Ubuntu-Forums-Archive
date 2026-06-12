---
title: "need help with grub 2 on windows 10 Ubuntu 14 dual boot"
date: 2016-08-19
forum: General Help
---

### Post by Gatorade on 2016-08-19
I have a hp pavillion x360 m1 , which I installed Ubuntu as dual boot along with windows 10. 

I don't get the GRUB menu to select Ubuntu.

I've been trying different grub rescue tutorials with no luck. 

can someone assist me with this please. these are the tutorials I was following

[https://sites.google.com/site/easylinuxtipsproject/6]("https://sites.google.com/site/easylinuxtipsproject/6")

[https://www.youtube.com/watch?v=i97y5Y2nChs]("https://www.youtube.com/watch?v=i97y5Y2nChs")

[https://www.youtube.com/watch?v=8lod8sRb_6I]("https://www.youtube.com/watch?v=8lod8sRb_6I")


I got Ubuntu to successfully install, but it just goes directly to windows every time.

---

### Post by oldfred on 2016-08-19
UEFI or BIOS?

Are both systems installed in UEFI, if Windows is UEFI?

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

      [/URL]
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file) 

Now if you have UEFI, you can run Boot-Repair's advanced mode and it will copy shimx64.efi to bootx64.efi and then you should be able to boot hard drive entry or fallback. Most HP are hard coded in UEFI to boot by description. And of course only valid description is "Windows Boot Manager". That is now allowed per UEFI standard. But fallback or hard drive entry also works.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by Gatorade on 2016-08-20
here's the link to the boot-info summary

[http://paste.ubuntu.com/23073193/]("http://paste.ubuntu.com/23073193/")


well, I read this on the first line , so I suspect this is where the problem is. 

"No boot loader is installed in the MBR of /dev/sda."

I tried the boot repair option before , but it didn't work , so I was hoping for someone to walk through it with me while I try to resolve the issue.

---

### Post by yancek on 2016-08-20
> 
"No boot loader is installed in the MBR of /dev/sda."

No, that is not the problem.  You are using EFI and you have a separate EFI partition (sda1), the first partition on the drive.  That is correct.  You also have the windows and Ubuntu efi files on that partition.  If you scroll about half way down you can see a number of messages about windows ntfs filesystem being in an unsafe state.  That means you left windows fast start or fast boot or hibernation on.  You see the message below repeated a number of times which is what you need to do:

> Please resume and shutdownWindows fully (no hibernation or fast restarting), or mount the volumeread-only with the 'ro' mount option.  

You could try the suggestion at the bottom of the boot repair.

---

### Post by Gatorade on 2016-08-21
thanks for the help guys. 
I will have to pick this up again in a few days when I get the time. I will report back when I get a chance.

---

### Post by Gatorade on 2016-08-25
I went into the windows settings and turned off the fast restart , there was no change , still boots directly to windows.

this model doesn't have the customized UEFI settings

still checking some of the other links posted by oldfred

---

### Post by oldfred on 2016-08-25
Boot-Repair's advanced mode will copy shimx64.efi to bootx64.efi so you can boot hard drive or fallback entry in UEFI (not Ubuntu). Most HP have a hard drive UEFI entry, if not we can add one.
       
 'Use the standard EFI file' in advanced options. 
     [https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)

But Boot-Repair sees all the HP .efi files in the ESP and adds a new 25_custom grub entry for all those. You may not want all or any of them. They are for HP utilities. 

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by Gatorade on 2016-08-25
[http://paste.ubuntu.com/23090198/](http://paste.ubuntu.com/23090198/)


still booting into windows.

tried the suggested fix in the command prompt, and it said "the boot configuration data store could not be opened."

---

### Post by oldfred on 2016-08-25
Have you tried booting this entry, I just do not know if BIOS or UEFI hard drive entry:

> Boot3001* Internal Hard Disk or Solid State Disk    RC If that does not work:

 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition  

Your install is sda1 or use sda & 1 or:
sudo efibootmgr -c -g -d /dev/sda -p 1 -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'

---

### Post by T2uiYKb7 on 2016-08-25
Would the following work?


[I]sudo  grub-install  --boot-directory=/media/[COLOR=#008000]liveuser[/COLOR]/[COLOR=#008000]UbuntuLabel[/COLOR]  /dev/sd[COLOR=#008000]x[/COLOR]
[/I]
Then browse to the /boot/grub.cfg file and add the needed entries.

It's worked for me in the past **but get a second opinion from another forum member before you do this.**

It sounds like grub needs to be reinstalled as it's being ignored in favour of Windows boot manager.

**Edit: **Forget the above I'm getting ahead of myself. **Can you take a screenshot of Disk Management? **(Control Panel > Administration Tools > Disk Management)

---

### Post by Gatorade on 2016-08-25
> **oldfred said:**
> Have you tried booting this entry, I just do not know if BIOS or UEFI hard drive entry:

If that does not work:

 sudo efibootmgr -c -g -d /dev/sdX -p Y -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
sdX is drive, Y is efi partition  

Your install is sda1 or use sda & 1 or:
sudo efibootmgr -c -g -d /dev/sda -p 1 -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'

I don't know where that is , " Boot3001* Internal Hard Disk or Solid State Disk RC " 
I don't see an option for that anywhere.


I don't know if I did it right , it's still just booting directly to windows.

---

### Post by oldfred on 2016-08-25
The last command if copied into terminal should add a new UEFI entry. "UEFI hard drive".
Then can you choose that?

---

### Post by T2uiYKb7 on 2016-08-26
If pressing Shift doesn't show the Grub menu and GRUB_HIDDEN_TIMEOUT= isn't set to 0 (and it's still not showing) then Grub is being ignored and the Windows Boot manager is being used. I doesn't matter what is in the grub.cfg in that case. (Maybe that's wrong.)

---

### Post by Gatorade on 2016-08-26
> ubuntu@ubuntu:~$ sudo efibootmgr -c -g -d /dev/sda -p 1 -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 
** Warning ** : Boot0003 has same label UEFI hard drive 
BootCurrent: 0000 
Timeout: 0 seconds 
BootOrder: 0004,2001,0001,0002,0003,2002,2004 
Boot0000* USB Hard Drive (UEFI) - SanDisk SDDR-113 
Boot0001* Windows Boot Manager 
Boot0002* ubuntu 
Boot0003* UEFI hard drive 
Boot2001* EFI USB Device 
Boot3001* Internal Hard Disk or Solid State Disk 
Boot0004* UEFI hard drive 
ubuntu@ubuntu:~$ 


I tried the line of code you suggested, but I'm still getting the same result.
Goes directly to windows, I don't get any option to choose anything.

---

### Post by Gatorade on 2016-08-26
> **andrew.nz said:**
> If pressing Shift doesn't show the Grub menu and GRUB_HIDDEN_TIMEOUT= isn't set to 0 (and it's still not showing) then Grub is being ignored and the Windows Boot manager is being used. I doesn't matter what is in the grub.cfg in that case. (Maybe that's wrong.)

When am I supposed to press shift? holding the shift key during start up does nothing.

---

### Post by oldfred on 2016-08-26
Shift is for BIOS boot. With Ubuntu it is the escape key.
But you want to get into UEFI boot menu or UEFI configuration menus.
Then you must use the key your UEFI is designed to use, and that varies by mfg.
Often f2 or del to get into UEFI. And directly to a UEFI boot menu is often f10 or f12. Some like HP use a combination of keys.

---

### Post by Gatorade on 2016-08-26
ok, I finally got it to work.

Fred , as you suggested, I hit the esc key on start-up , which brings me to a start-up menu , F9 gives me the boot device options where I found the boot manager.
From there I can boot into Ubuntu.

It's a lot more steps to boot into Ubuntu, though. This laptop belong to a friend, and I'm hoping this isn't too much trouble for her.

My computer loads the GUB menu , which I can select windows or linux, and loads linux by default if I don't touch anything.
This is how I wanted to set up this HP laptop, but I guess I can live with a couple extra button clicks, lol.


thank-you so much for the help everyone.

---

