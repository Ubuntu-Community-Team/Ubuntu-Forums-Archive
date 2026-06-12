---
title: "dual boot with Win 8.1 suddenly stopped"
date: 2014-09-11
forum: General Help
---

### Post by mmcl26554 on 2014-09-11
I have an HP Envy touch screen laptop with win 8.1.  I successfully installed Ubuntu 14.04 in July and I got the grub menu to work fine.   Well then it stopped showing up but I could still get into Ubuntu by pressing the F9 key and going to the alternate device menu, Ubuntu was there and when I clicked on it Grub came up and I could boot Ubuntu.  I learned about and switched over to rEFind and it worked well, I liked it!   Now, however, that too has stopped working.  I was in contact with the maintainer of rEFind but the suggestions he made didn't work.  I'm totally stumped!   As a beginner I don't have a lot of skill with Ubuntu but I am learning it in an attempt to keep my aging brain active.   Before I posted this I did do a search of the forum but didn't find much.   I would expect there to be a lot of posts about dual booting win 8.1 but I didn't find them.  Maybe my search key words were just wrong.  Anyway I need some help.
Michael

---

### Post by oldfred on 2014-09-11
Have not seen Rod in this forum for ages, but he knows more about booting than just about anyone. If his suggestions did not work, not sure we can do much else. Plus he is the creator of rEFInd and would know a lot more about it.

You can run Boot-Repair, but do not run any fixes, not even sure if it would fix anything if rEFInd installed. Just run the report and post the link it gives so we can see details of your install.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mmcl26554 on 2014-09-11
I ran boot repair and here is the address to view the results:  [HTML]http://paste.ubuntu.com/8322676/[/HTML]
My problem with Rod is actually with me, I do not clearly understand what he wants me to do, I am just to much of a beginner and therefore I don't get what he is asking me to do.   So that is why I have come here because the directions are generally something I understand.   I know he is the guru of this but I'm just not smart enough with Ubuntu to follow him.
Michael

---

### Post by oldfred on 2014-09-11
I have not installed nor dealt with rEFInd, although I have suggested to others to use it. Many have commented that it works well.

A lot of what I learned about gpt and UEFI was from him, so I am not sure I can help much more.

HP only wants to boot Windows, so you have to have a work around to get it to boot Ubuntu. REFInd is one of the suggested work arounds, but many have just renamed the bootx64.efi file in the efi partition to really be grub and boot hard drive entry in UEFI menu.

 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
      
 HP Manually renamed files to make it work.
[URL="http://ubuntuforums.org/showthread.php?t=2131886"]http://ubuntuforums.org/showthread.php?t=2131886

      [/URL]
 HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)


 Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.

 
    [URL="http://ubuntuforums.org/showthread.php?t=2131886"]
[/URL]

---

### Post by mmcl26554 on 2014-09-11
Fred,
This is what Rod wants me to do but I don't understand it enough to do it.  Could you explain it for me please:

 [FONT=arial][SIZE=2]**"One thing you could try doing is copying (not moving; create a fresh copy of) rEFInd in EFI/BOOT/bootx64.efi. With that done, wipe the list of boot loaders clean (except maybe the rEFInd entry or entries for booting from external media). This might force the firmware to boot using the default/fallback name (EFI/BOOT/bootx64.efi), which should be rEFInd."**[/SIZE]
[/FONT]
I get the wiping the list but the creating a fresh copy of what and how to do that.  Then am I supposed to replace the bootx64.efi or add another file to the EFT/BOOT/ folder?

Michael

---

### Post by oldfred on 2014-09-11
First backup the entire current efi partition. It is not really large so should be easy to do.

Sounds similar to the suggestion of copying grub's efi files to bootx64.efi. That file is the default boot for UEFI for the hard drive.

Not sure how you create new rEFInd entry.

You show these efi boot files from your BootInfo report starting at line 29. Plus many others for HP & Windows.
 /EFI/Acronis/bootwiz.efi
 [COLOR=#ff0000]/EFI/Boot/bootx64.efi [/COLOR]
 /EFI/Microsoft/bootmgfw.efi
 /EFI/refind/MokManager.efi 
[COLOR=#b22222]/EFI/refind/grubx64.efi [/COLOR]
 /EFI/refind/shimx64.efi 
 /EFI/ubuntu/MokManager.efi 
[COLOR=#b22222]/EFI/ubuntu/grubx64.efi [/COLOR]
 /EFI/ubuntu/shimx64.efi 

UEFI systems all seem to boot this entry as a default for a hard drive.
/EFI/Boot/bootx64.efi 

So both my previous suggestion of moving grub or moving rEFInd's grub to that folder and renaming it to bootx64.efi are that same.  Not sure if rEFInd has another file you want to copy. 
You should be able to experiment with either or all alternatives.

The issue is from live installer DVD or flash drive how you see that partition and each folder in the partition.

This will mount your sda3 efi partitioin to a default /mnt that already exists.
      
 From live installer mount the efi partition on hard drive:
mount /dev/sda3 /mnt
This will copy all the ubuntu efi files into the Boot folder:
cp /mnt/EFI/ubuntu/* /mnt/EFI/BOOT
This will rename the grub file to be the default hard drive UEFI boot entry.
mv /mnt/EFI/BOOT/grubx64.efi /mnt/EFI/BOOT/bootx64.efi

Then in UEFI choose to boot the hard drive entry.

    
You may want to do this separately or after restoring the backup so you do not mix up ubuntu's grub and refind's grub files. Not sure if same or not.
This will copy all the refind efi files into the Boot folder:
cp /mnt/EFI/refind/* /mnt/EFI/BOOT
This will rename the grub file to be the default hard drive UEFI boot entry.
mv /mnt/EFI/BOOT/grubx64.efi /mnt/EFI/BOOT/bootx64.efi

---

### Post by mmcl26554 on 2014-09-12
Thanks I believe I get it now.  Main thing is I have to boot the computer with a live USB to copy the files, because I cannot do it when Ubuntu on the hard drive is booted.  Is this correct?
Michael

---

### Post by oldfred on 2014-09-12
Yes, boot DVD or flash drive in live mode.
Then you have to mount partition to be able to work with it.

Not sure if Nautilus file browser would let you do anything or not. But you probably would have to start it from terminal with gksudo nautilus, but live installer does not normally use sudo and I think now does not even have the gksudo which you should use with gui apps.

---

### Post by mmcl26554 on 2014-09-12
> **oldfred said:**
> Yes, boot DVD or flash drive in live mode.
Then you have to mount partition to be able to work with it.

Not sure if Nautilus file browser would let you do anything or not. But you probably would have to start it from terminal with gksudo nautilus, but live installer does not normally use sudo and I think now does not even have the gksudo which you should use with gui apps.
So does that mean I need to do something other than your suggested in your previous post?
Michael

---

### Post by oldfred on 2014-09-12
Did you try them yet? It should work.
If you have good backup, then it does not matter what you do even if you make a mistake. But backups are important to make sure you have a way to go back.

---

### Post by mmcl26554 on 2014-09-13
Not yet, I was just a little confused by your statement "[COLOR=#000000][I]gksudo nautilus, but live installer does not normally use sudo and I think now does not even have the gksudo which you should use with gui apps", and wondered if there is something different I should do.   I do have a back of all partitions on the drive and it was made when things were working.   I use Acronis, which I really don't like the newest versions of.   I tried restoring the sda3 partition but it didn't make any difference, OR Acronis didn't actually restore it.   If it should have gotten it working again, then I'll delete the contents of the partition and try the restoration again.  I do this using a disk with Acronis on it so the computer doesn't have to boot from the hard drive.  Please tell me what you think about this.  It would be easy to do if it is expected to fix things.
Michael[/I][/COLOR]

---

### Post by oldfred on 2014-09-13
I have not used Acronis.
My backup is just a copy of all the folders/files I think I may need. I use rsync & just copy to another drive. And copy to a flash drive. And copy to a DVD. Usually at different times and some different data.

It used to be that you could do just about anything with Nautilus from liveCD. But I think with new versions, it does not automatically let you do that. I have not used live flash drive or anything recently as I have several installs on different drives and use those in case I need external maintenance.

The Nautilus suggestion was just another alternative to try. The command line process should work.

---

### Post by mmcl26554 on 2014-09-13
Do you have any thoughts on restoring the whole EFI partition as a likely fix?
Michael

---

### Post by oldfred on 2014-09-13
You need the rename of bootx64.efi. Either Ubuntu's grub or rEFInd's grub.
Have you tested the rename?

The backup is just in case something has major issues.

---

### Post by mmcl26554 on 2014-09-15
Although I haven't yet tried what you suggested I did read an article about running Ubuntu from a "Virtual Box".   Does this work well?  Is it a good way to work around the UEFI problems I am plagued  with by my buggy HO computer?
Michael

---

### Post by oldfred on 2014-09-16
Some like the Virtual install. 
If you have more RAM and newer processor it supposedly runs well. But I have only dual booted with my system. Do not know how it works with UEFI.

Frankly if you are having issues copying a file or two in another partition, you may have some challenges in configuring a Virtual install. There are instructions, but it requires some configuration and installing of packages to make it work.

---

### Post by mmcl26554 on 2014-09-16
Fred, I'm not having any great issues copying the files, I just haven't had the time to deal with it yet.   My Wife recently got out of the hospital after the big medical center to the north (UPMC) botched a simple routine liver biopsy and just about killed her.  Now they scared her with what they think is a newly discovered heart issue which in reality has been with her all her life.   So I've had to spend a lot of time supporting her.  I just haven't had the time to focus on Ubuntu and devote the necessary time to do it.   I have other things on my mind right now.  But I'll get to as she is improving.
Michael

---

### Post by oldfred on 2014-09-16
Hope your wife is doing better.
And of course issues in life are more important.
We will be here when you get back to working on Ubuntu fixes.

---

### Post by mmcl26554 on 2014-09-20
> **oldfred said:**
> First backup the entire current efi partition. It is not really large so should be easy to do.

Sounds similar to the suggestion of copying grub's efi files to bootx64.efi. That file is the default boot for UEFI for the hard drive.

Not sure how you create new rEFInd entry.

You show these efi boot files from your BootInfo report starting at line 29. Plus many others for HP & Windows.
 /EFI/Acronis/bootwiz.efi
 [COLOR=#ff0000]/EFI/Boot/bootx64.efi [/COLOR]
 /EFI/Microsoft/bootmgfw.efi
 /EFI/refind/MokManager.efi 
[COLOR=#b22222]/EFI/refind/grubx64.efi [/COLOR]
 /EFI/refind/shimx64.efi 
 /EFI/ubuntu/MokManager.efi 
[COLOR=#b22222]/EFI/ubuntu/grubx64.efi [/COLOR]
 /EFI/ubuntu/shimx64.efi 

UEFI systems all seem to boot this entry as a default for a hard drive.
/EFI/Boot/bootx64.efi 

So both my previous suggestion of moving grub or moving rEFInd's grub to that folder and renaming it to bootx64.efi are that same.  Not sure if rEFInd has another file you want to copy. 
You should be able to experiment with either or all alternatives.

The issue is from live installer DVD or flash drive how you see that partition and each folder in the partition.

This will mount your sda3 efi partitioin to a default /mnt that already exists.
      
 From live installer mount the efi partition on hard drive:
mount /dev/sda3 /mnt
This will copy all the ubuntu efi files into the Boot folder:
cp /mnt/EFI/ubuntu/* /mnt/EFI/BOOT
This will rename the grub file to be the default hard drive UEFI boot entry.
mv /mnt/EFI/BOOT/grubx64.efi /mnt/EFI/BOOT/bootx64.efi

Then in UEFI choose to boot the hard drive entry.

    
You may want to do this separately or after restoring the backup so you do not mix up ubuntu's grub and refind's grub files. Not sure if same or not.
This will copy all the refind efi files into the Boot folder:
cp /mnt/EFI/refind/* /mnt/EFI/BOOT
This will rename the grub file to be the default hard drive UEFI boot entry.
mv /mnt/EFI/BOOT/grubx64.efi /mnt/EFI/BOOT/bootx64.efi


Wife is improved, saw her Primary Care Physician, who was no where near as excited about it as the "Zebra Hunters" at UPMC were so she is feeling much better about the whole thing.

Now for Ubuntu, I got an error message right off the bat:
[/CODE]ubuntu@ubuntu:~$ /mount/dev/sda3/mnt
bash: /mount/dev/sda3/mnt: No such file or directory
ubuntu@ubuntu:~$ [/CODE]
Did I do something wrong?
Michael

---

### Post by oldfred on 2014-09-20
This:
/mount/dev/sda3/mnt
Should be this:
mount /dev/sda3 /mnt
Spaces become important. Often better to copy & paste commands into terminal.
See also 
man mount

Glad to hear wife is doing better. :)

---

### Post by mmcl26554 on 2014-09-21
I did notice the space after the sdb3  and that didn't work because I didn't notice the space after mount  .  So I'll try that and post back.   Well, I guess that's what I'm here for, to learn!
Michael.

---

### Post by mmcl26554 on 2014-09-21
Well, that didn't fix it.   I had to use sudo to run the commands but that should be ok?
I ran another boot repair summary just in case it would be helpful.  Should I try to run boot repair to see if it will fix it.   I don't care if rEFind works or not if Grub does.
```
http://paste.ubuntu.com/8398097/
```

Michael

---

### Post by oldfred on 2014-09-21
What specifically did not work.

The copy of grubx64.efi and rename to bootx64.efi has worked for just about everyone. I just do not know which grub you have with rEFInd. Did you try both the one in Ubuntu folder and the one in the refind folder?
And you have to change boot in UEFI to boot hard drive, or use one time boot key to boot hard drive.
And if copying grubx64.efi you have to have secure boot off.

---

### Post by mmcl26554 on 2014-09-21
What I meant was.  Although the changes did happen it had no effect on the outcome,  That is, it still booted to windows.   I did the changes from a live boot of Ubuntu and when it didn't work I tried it from Ubuntu on the hard drive, by making Nautilus root.   I made all the changes again but no go.   Maybe windows is booting with ```
bootmgfw.efi
```
Is it possible that the problem lays there?   I have set windows to use the boot manger in Ubuntu but it doesn't make any difference.    It did make a difference when I first installed Ubuntu but not anymore.   Also any changes I make to boot manager in Ubuntu get changed back to where they were with the next boot.  So I'm stumped!  
Michael

---

### Post by oldfred on 2014-09-21
Windows will always want to be the default boot manager.

In UEFI or one time boot key, you have to select hard drive. The bootx64.efi is the one that refers to hard drive and system will let that boot. But UEFI has been modifed to only otherwise boot Windows entry in UEFI.
So if bootx64.efi is really the grubx64.efi file then booting hard drive actually boots grub menu.

---

### Post by mmcl26554 on 2014-10-15
I have not been able to fix this, that's the bad news, the good news is the whole dual boot installation was on a different drive other than the original one.   The original drive has win 8.1 on it which I have kept up to date.  So I have installed it and then installed Ubuntu 14.04 in a Virtual Box.  Actually this has great potential to be what I want,  BUT I'm having some problems which I will ask for help with on a new thread.  
To those of you which offered assistance even though it didn't work out I learned some things so thanks for your help.
Michael

---

