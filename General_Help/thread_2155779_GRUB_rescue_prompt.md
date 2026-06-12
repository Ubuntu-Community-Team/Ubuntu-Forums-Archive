---
title: "GRUB rescue prompt?"
date: 2013-06-19
forum: General Help
---

### Post by cookbook on 2013-06-19
After rebooting my 12.04, I was met by this GRUB rescue prompt

grub rescue>

I looked up what others did, however it has been ineffective

ls gives me
(hd0), (hd0,msdos2), (hd0,msdos1)

and set gives me
prefix = (hd0,msdos1)/boot/grub
root = hd0, msdos1

Can someone please help me boot or fix this?

---

### Post by cookbook on 2013-06-19
[INDENT]                     After rebooting my 12.04, I was met by this GRUB rescue prompt

```
 grub rescue> 
```

I looked up what others did, however it has been ineffective

ls gives me
```
(hd0), (hd0,msdos2), (hd0,msdos1)
```

and set gives me
```
prefix = (hd0,msdos1)/boot/grub
root = hd0, msdos1
```

Can someone please help me boot or fix this?                 
[/INDENT]

---

### Post by coffeecat on 2013-06-19
Threads merged. Please do not post the same thing in different parts of the forum.

---

### Post by sum1nil on 2013-06-19
Please excuse any duplicate info :) 
______________________________

If you type 'ls' as a command you will get a list of your hardrives. You can then go then iterate through them using, for example, 'ls (hd0,msdos1)/[tab]' to get a listing of what is on that drive. Initially you are looking for your bootloader to display the grub filesystem. This would be your boot drive. Keep iterating through them to see which is your root drive which would have the typical filesystem. This of course is your boot drive. for example 'ls (hd0,msdos2)/<tab>;

So for example, if (hd0,1)/ is your boot drive enter the command ignore the <>'s:
'linux (hd0,msdos1)/vm<tab - and your kernel should show up as an image> ro root=/dev/hda2 <or whatever the root happened to be> rdshell'

*rdshell should drop you to a diagnostic if say hdXX fails to be mounted. But you should have the proper partition after iterating through all the drives.

'initrd (hd0,msdos1)/initram<tab>' to make sure to establish your ram drive.

Then type 'boot'.

Remember, you are looking for filesystem structures not partitions.
This is only very basic knowledge of the grub rescue system, searching will give you plenty of more details and you may want to download SuperGrub ISO.

If all goes well and you enter linux, I would not simply use 'grub-update' but 'grub-install /dev/hda' (or whatever is the real boot drive) to reinstall grub on the volume.

Best of luck.

---

### Post by oldfred on 2013-06-20
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by cookbook on 2013-06-20
How can I find which one is my typical filesystem? When I browse through the directories using ls, they all have identical directories, inside both /dev and /boot/grub. It says there would be dozens of .mod files, but all of the files in the /boot/grub are identical, even in the (hd0).

---

### Post by oldfred on 2013-06-20
If you have gone thru the 6 or seven boot commands in drs305's thread for both (hd0,1) or sda1 and (hd0,2) or sda2, then you have other issues and need Boot-Repair.

---

