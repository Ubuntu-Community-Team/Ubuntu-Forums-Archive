---
title: "How to control the default version loaded when several versions on one computer?"
date: 2014-10-29
forum: General Help
---

### Post by Tom_Carr on 2014-10-29
I have installed ubuntu and kubuntu on one computer.   When I startup, there is a screen that will let me select which version runs, but if I don't select a version, the defalut is kubuntu, which is the last one I installed.  Is there a way to change this so ubuntu is the default?

---

### Post by vasa1 on 2014-10-29
My understanding is that the last selected DE, whichever that may be, is the one that runs if you just enter your password and hit enter.

---

### Post by ajgreeny on 2014-10-29
Simply boot to Ubuntu and run command ```
sudo grub-install /dev/sda
``` to make Ubuntu the OS that is in charge of the grub bootloader.

If you have more than one hard disk you must obviously point that command to the device with boot priority, but I assume from your post it's a single disk machine.

---

### Post by deadflowr on 2014-10-29
^+1.
Something more to chew on.
Sometimes whenever you get a newer package for grub, it'll most likely reinstall grub for that system, overwriting the exist grub-install.
(It's very rare to get new grub packages, but it can happen)
So if you do notice an update to grub, or the boot menu changed on bootup, don't be alarmed.
Simply re-run the grub-install command again from the system you want to control grub.
(There is a more complex way to re-install it from within the "Other system", but booting into the one you want is way easier, IMO.)


Another thing to note, is that if the second system(Kubunjtu) ever gets a new kernel-update, it[the newer kernel number] won't be listed in grub until you re-run the command
*sudo update-grub* 
on the main(Ubuntu) system.
If you get a new kernel on the main system(Ubuntu), grub will be updated during the kernel's installation, so you won't need to run the update command, in that case.

Hope that helps, and hope that makes sense.

---

### Post by Tom_Carr on 2014-10-29
Thanks for the info.  One more related question before I close out this thread.  Will all of this still be true if I install Mint on the same machine?  It is a single drive machine.

---

### Post by Dennis N on 2014-10-30
There is more to it:

The default in the grub menu is the first menu entry unless you specify otherwise in **/etc/default/grub** by changing the value of GRUB_DEFAULT. Setting to zero (GRUB_DEFAULT=0) makes the first menu entry start if you do nothing. That is the default setting. Setting to GRUB_DEFAULT=1 will start the second menu entry if you do nothing. These changes are made in this file on the OS which controls grub (i.e., the OS that installed it). Changing values here requires sudo.

After changing any values in **/etc/default/grub**, you must run **sudo update-grub** to make them take effect.

If you start using more than two installations on a disk, you may be better served by a custom grub menu that requires no maintaining by you:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by yancek on 2014-10-30
The default for the installation of the Grub bootloader on all these systems is to install to the master boot record of the first drive.  If you want to keep the Ubuntu Grub bootloader in the master boot record, you would install Grub for your new Mint installation to the same partition as you install Mint.  This is a very simple process during installation and has worked for me dozens of times with Ubuntu and derivatives.  Otherwise, you need to go through the process described above each time.  The simplest other option is the suggestion by ajgreeny above.

---

### Post by Dennis N on 2014-10-30
Everything described in the posts here is fine for a traditional BIOS system. But, what if the system is UEFI? I believe that a GRUB installation in  UEFI mode would only be allowed on an EFI system partition since it requires the installation of an entire folder. 

In this case, each of the particular OSes used happens to name its folder in the system partiton 'ubuntu' (that includes Mint at the present time) resulting in folders from the previous installs being overwritten. So you are stuck with the most recent install controlling grub. Is there a way around this? The procedure in post #7, although fine for traditional BIOS, would not be possible. Just posing the question.

---

### Post by mcduck on 2014-10-30
> **Dennis N said:**
> There is more to it:

The default in the grub menu is the first menu entry unless you specify otherwise in **/etc/default/grub** by changing the value of GRUB_DEFAULT. Setting to zero (GRUB_DEFAULT=0) makes the first menu entry start if you do nothing. That is the default setting. Setting to GRUB_DEFAULT=1 will start the second menu entry if you do nothing. These changes are made in this file on the OS which controls grub (i.e., the OS that installed it). Changing values here requires sudo.

After changing any values in **/etc/default/grub**, you must run **sudo update-grub** to make them take effect.

If you start using more than two installations on a disk, you may be better served by a custom grub menu that requires no maintaining by you:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

even more useful than setting the default number, in many cases, is to set the GRUB_DEFAULT to *saved* and then GRUB_SAVEDAFAULT to *true*. This will make Grub default to booting the OS you used last time.

---

### Post by mcduck on 2014-10-30
> **Dennis N said:**
> Everything described in the posts here is fine for a traditional BIOS system. But, what if the system is UEFI? I believe that a GRUB installation in  UEFI mode would only be allowed on an EFI system partition since it requires the installation of an entire folder. 

In this case, each of the particular OSes used happens to name its folder in the system partiton 'ubuntu' (that includes Mint at the present time) resulting in folders from the previous installs being overwritten. So you are stuck with the most recent install controlling grub. Is there a way around this? The procedure in post #7, although fine for traditional BIOS, would not be possible. Just posing the question.
Even with BIOS boot, the most recent install is the one controlling Grub, as Ubuntu's installer will install Grub as well unless you specifically tell it not to, and that would overwrite the Grub install from previous version.

So in both cases any edits to Grub must be made from the Ubuntu install that is controlling Grub, in most cases the last installed one.

---

### Post by Dennis N on 2014-10-30
> **mcduck said:**
> Even with BIOS boot, the most recent install is the one controlling Grub, as Ubuntu's installer will install Grub as well unless you specifically tell it not to, and that would overwrite the Grub install from previous version.

So in both cases any edits to Grub must be made from the Ubuntu install that is controlling Grub, in most cases the last installed one.

With BIOS, if you install grub to the OS partition (sda3 for example, if that is where the new install is located) instead of the MBR (sda), you don't overwrite the MBR entry of the previous GRUB so the previous grub.cfg is still in control. This is what yancek is suggesting in #7. I have been doing this for years without any problems.

Added info:
In this case, to keep the older grub, you need to manually add a custom grub menu entry for the new OS in the older system.

---

### Post by Dennis N on 2014-10-30
> **mcduck said:**
> even more useful than setting the default number, in many cases, is to set the GRUB_DEFAULT to *saved* and then GRUB_SAVEDAFAULT to *true*. This will make Grub default to booting the OS you used last time.

Is this option working now? This was brought up in this post some time ago and it was broken:

[http://ubuntuforums.org/showthread.php?t=2193538](http://ubuntuforums.org/showthread.php?t=2193538)

---

### Post by mcduck on 2014-10-30
> **Dennis N said:**
> Is this option working now? This was brought up in this post some time ago and it was broken:

[http://ubuntuforums.org/showthread.php?t=2193538](http://ubuntuforums.org/showthread.php?t=2193538)

I've never noticed it been broken, I have been using the option (and the equivalent option before Grub2) in every Ubuntu install I've used without any issues. I have no idea what might have caused the problem for the suer in that thread, but it definitely is working, and should have been working even back then... MUst have been some machine-specific problem or something like that.

---

