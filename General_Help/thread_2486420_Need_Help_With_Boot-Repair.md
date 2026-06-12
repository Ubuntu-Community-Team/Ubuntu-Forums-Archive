---
title: "Need Help With Boot-Repair"
date: 2023-04-29
forum: General Help
---

### Post by arius88 on 2023-04-29
Anybody able to help me navigate boot-repair's advanced options?

A bandmate recently gave me a computer with Windows 7 Professional  (BIOS) on it. I need to keep Windows on the machine because it contains the professional versions of two expensive programs that he uses to record, mix, and master our songs.  

However, I prefer Linux, so I decided to turn the computer into a  dual-boot machine. Huge mistake. I was able to partition the drives and install  Lubuntu; Lubuntu works great. However, now I can't boot into Windows. Windows 7 is definitely still on the machine - I can even see all the files in my Lubuntu file manager - but something is preventing it from booting. If  I press F12 on startup, a menu comes up with an option to boot Windows  7. I click on it, and I get an error. "Windows failed to start. A recent  hardware or software change might be the cause." It then prompts me to  install a Windows installation disk, which I don't have. It gives me two  other potentially useful pieces of information:

Status: 0xc0000225

Info: The boot selection failed because a required device is inaccessible.

Obviously the Lubuntu install changed something that is causing Windows not to boot. But I have no idea what. 

So I installed and ran boot-repair in Lubuntu. It created new options in a boot menu for me to boot windows from sda1 or sda2, but neither of the options actually boots windows. The first (on /dev/sda1) leads to a cursor that blinks for forever without doing anything, the second (on /dev/sda2) leads straight to the error page stating that "Windows failed to start. A recent  hardware or software change might be the cause."

I'm now considering tinkering with boot-repair's advanced mode, but I'm terrified of doing something wrong and making my problem worse or even unfixable. I can't find any resources online about how to safely navigate boot-repair's advanced options. The manual just says to ask someone who knows what they are doing for help.

Before I make a horrible mistake, just want to confirm. Under the "GRUB location" tab, it says: OS to boot  by default. It was listing sda4. There are two other options aside from  sda4.  One is "sda1: Windows 7 (boot) (via sda4 menu)" and the other is  "sda2: Windows 7 (via sda4 menu)." I assume I want to boot sda1?

Under the "Main Options" tab, there are unselected options to Restore  MBR and to Repair file systems. I'm wondering if I should select those  as well. I really don't know if Windows was using a Master Boot Record or not, or how to find out that information. But I'm guessing Lubuntu wrote its own boot stuff over top of the Windows boot stuff and I suspect the Restore MBR thingy may be the ticket. 

Here's my most recent boot-repair pastebin, in case that's useful: [https://paste.ubuntu.com/p/fXr8JNCmMn/](https://paste.ubuntu.com/p/fXr8JNCmMn/)

Would really appreciate any help. Feeling pretty stuck at this point. I'm disabled and broke AF but may need to call in a professional if I can't get boot-repair to work.

---

### Post by oldfred on 2023-04-29
As previously posted, Boot-Repair is a tool to fix Linux systems, not Windows.
It does do some minor fixes with Windows and may be able to install a Windows type boot loader. But that will never be the default fix.
You would need a Windows repair flash drive to fix Windows.

Did you not try the suggestion in your previous thread,  post #30?
[https://ubuntuforums.org/showthread.php?t=2485992&page=3](https://ubuntuforums.org/showthread.php?t=2485992&page=3)

---

### Post by yancek on 2023-04-30
>   OS to boot  by default. It was listing sda4. 

You seem to be confusing which partition to boot first which i what the above states, with where to install Grub.  The OS to boot by default simply sets a specific OS to boot by default in the Grub menu and does nothing about installing Grub to any specific location.  

I'm not sure if I asked this in your other thread but, did you ever boot windows 7 on this computer successfully prior to installing Lubuntu?

Have you tried using GParted to set the boot flag to the windows 7 boot partition (sda1) and rebooting to test?  If it fails, set the boot flag to sda2 to test if it boots.
Also, have you tried the suggestion by oldfred in your other post?

If these options fail, you will need to get a windows 7 recovery disk.  They used to be readily available online but since 7 is long out of support, that may be more difficult.  
As oldfred has pointed out, boot repair is to repair "LInux" systems.  What boot repair does for windows is to create an entry in the grub.cfg menu for windows.  This is a 'chainload' entry which simply points to the location (PBR) on the windows active partition where the boot files "should" be and then windows boots.  The proper boot files seem to exist on your partitions for windows so the problem is, are they in the wrong location or are they corrupteds?  In either case, you need a windows recovery tool.  Good luck!

---

### Post by arius88 on 2023-04-30
Nice to see the old gang all back together again!

Since apparently I need a Windows recovery tool and not boot-repair, I'm going to shut down this thread and move back to the original thread. I appreciate the clarity on that. It now makes sense why Fred kept saying that boot-repair only boots working Windows. I didn't get it before. 

Before I go, I'll just respond to the questions asked here.

1. I did do my best to do the things in oldfred's post #30. However, the stuff I was able to figure out how to do didn't work for me. I don't remember why.
2. Yes, Windows 7 worked beautifully precisely until I tried to make the machine dual-boot. (I actually tried to install POP_OS first, which is my preferred OS, but that install failed and I gave up after a few days of frustration and installed Lubuntu.)
3. I forget if I tried setting the boot flag to sda2. I think I did do that, but I will try again just to be sure.

---

