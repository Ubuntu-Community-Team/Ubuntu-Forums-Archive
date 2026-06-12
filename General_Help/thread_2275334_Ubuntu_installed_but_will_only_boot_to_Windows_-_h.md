---
title: "Ubuntu installed but will only boot to Windows - help please"
date: 2015-04-25
forum: General Help
---

### Post by michael-piziak on 2015-04-25
I installed Ubuntu 12.04 LTS from a thumb drive and it installed successfully on half the computer  ; however, it will only boot into Windows 8 when turned on.

I can force it to boot into Ubuntu if I hit escape upon boot and choose boot option then choose Ubuntu; however, we want this laptop to boot directly into Ubuntu (or atleast give the option of which OS to boot into).

I typed 
sudo grub-install /dev/sda

into terminal from [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

but it still boots into Windows 8

Help please.

This computer is an HP 2000 Notebook PC

---

### Post by Bucky Ball on 2015-04-25
*Thread moved to **General Help**.*

Try Boot Repair. That might help. 

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by michael-piziak on 2015-04-25
Thanks for your prompt reply.

I typed in the 3 terminal commands and Boot Repair did what it would do; however, it still boots into Windows 8.  Right before it goes into Windows 8 one sees a brief flash of the Ubuntu OS, but no option to go into Ubuntu still.

Still looking for a solution.

p.s. If I just let Ubuntu 12.04 LTS install 100% of itself on this laptop, would that work or would it turn this laptop into an unusable brick - ?

p.s.s. If I let this computer update itself to Ubuntu 14.04 LTS now would that maybe fix the problem - ?

---

### Post by Bucky Ball on 2015-04-25
Have you tried hitting the shift key just after boot? That should bring up the grub menu, if it's there, and if they haven't changed the key.

---

### Post by michael-piziak on 2015-04-25
If I can get to the grub menu, do I make a selection or type something in ?

I will try to get into the grub menu now.  

I appreciate the help because I'm at my Aunts house for a few more hours and do hope to get Ubuntu working for her - because Windows 8 she can't use it's such a piece of trash OS.

---

### Post by michael-piziak on 2015-04-25
Update:  the shift key can't get me to grub; however

I can get to a grub menu by tapping escape, giving me a startup menu, then going to the boot option menu.  I can then get to Ubuntu Grub.

What do I do at that point ?

Also, again, would installing Ubuntu 12.04 lts on 100% of this computer - would that force the computer to boot into Ubuntu or is there something in the bios that wants WIndows 8 and would render the system into an unusable brick?

---

### Post by ajgreeny on 2015-04-25
As this is a Windows 8 machine my suspicion is that the Windows OS is installed using UEFI, but unless you were aware of that fact and installed accordingly, you probably installed Ubuntu in legacy BIOS mode.  The two do not live together I'm afraid; both OSs must be installed in the same mode, either UEFI or BIOS, but not one of each, and you will have to take some action to overcome the problem.  If you have not used Ubuntu it may simply be quickest to install again, making sure you boot the USB install medium in UEFI mode, meaning that you then install in that same mode.

Run Boot-Repair again but this time simply get the report it produces and show us the pastebin link that you are given for that.  It should show us all the details of the problem and suggest ways to overcome it.

---

### Post by michael-piziak on 2015-04-25
In one of the startup menus, there is an option to boot from a UFI file - but with my USB thumb drive in, I'm not quite sure how to get Ubuntu to install from there.

I'm using Ubuntu 12.04 LTS on this system now, I just have to hit escape and go through several menus to boot.

I will get the report from boot repair and reply back very soon.

I'm still wanting this question answered:  Can I just install Ubuntu on the entire computer from the USB device and get Ubuntu to book then?  Or is this UFI thing even stopping that option - ?

---

### Post by michael-piziak on 2015-04-25
Update:  this is the boot repair report:

Please write on a paper the following URL:
[http://paste.ubuntu.com/10889758/](http://paste.ubuntu.com/10889758/)


If you are experiencing boot issues, indicate this URL to people who help you. For example on forums or via email.

---

### Post by westie457 on 2015-04-25
```
[COLOR=#000000]sda4: __________________________________________________________________________[/COLOR]
    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr  [COLOR=#000000]                       /ubuntu/winboot/wubildr.mbr[/COLOR]
```

Have not looked at the whole report however the above is probably the main cause of your problems.

Wubi does not work with Windows 8 or a hard drive with a GPT partition table.


One solution is to uninstall Ubuntu from inside Windows and do a fresh installation from the start.


Before attempting to install another OS you must disable Windows FastStartup. This is found in Control Panel > Power Options > Choose what the power button does > Show settings that are not available. While there disable Hibernation. 

Next use Windows tools to defrag the hard drive and then shrink the Windows partition. Reboot Windows just in case of issues regarding the resize of the Windows partition.

Edit
When Windows is installed using UEFI, Ubuntu (or any other OS) must be installed the same way.

---

### Post by michael-piziak on 2015-04-25
I'm not sure what Wubi is.  I do know that I'm using Ubuntu 12.04 LTS right now on the notebook, I just want it to boot into it.

So I take it that I can't simply install 12.04 LTS on the entire hard drive with the USB and expect it to work - ?

Please advise how I uninstall Ubuntu from within Windows as you suggested - ?

Right now I'll disable Windows FastStartup and disable hibernation from within Windows 8.  Then where do I go from there?

---

### Post by michael-piziak on 2015-04-25
Update:  I turned quick start up off in Windows and hibernation wasn't selected.

---

### Post by westie457 on 2015-04-25
To uninstall Wubi from Windows.
Control Panel > Programs and Features. Find Ubuntu in the list select and click Uninstall.

Not 100% sure that the Grub files will be removed from sda2. If they are not removed they will have to be manually removed. However I have never tried to edit anything in that partition. Oldfred probably knows a way, hopefully he joins this thread and can explain the process to edit those files.

---

### Post by michael-piziak on 2015-04-25
If I remove Ubuntu from within the Windows environment, what is the next step as I'm still using Ubuntu to get on the internet.

Please someone tell me I can simply take my USB thumb drive and wipe out the entire HD and put only Ubuntu on it and it will work.   All this going into Windows 8 and fiddling around is annoying as I'm not a Windows 8 user and nothing seems to be where it should be in Windows 8.  Also, I'm only at my Aunts house a few more hours.

---

### Post by ajgreeny on 2015-04-25
From your boot-repair report it looks as if you have used a proper partitioned installation, not a wubi install.  It also looks as if this computer is an HP model, which could be a main cause of your problem as HP have tweaked their UEFI to allow only a windows efi bootloader to boot the system, not any other OSs.  This can be overcome by renaming the ubuntu efi bootloader but I do not have the details at the moment so will have to come back with that info for you unless oldfred does so before I get back here.

---

### Post by michael-piziak on 2015-04-25
Thanks to all that helped.

I had limited time at my Aunts house, so I went ahead and reinstalled Ubuntu 12.04 LTS on the entire HP laptop and completely wiped out Windows 8.

It was a gamble I guess, but it paid off.  Now Ubuntu works perfectly on her system and she can actually use it now (after 2 years of having Windows 8 frustrate her).

Thanks again !

---

### Post by Bucky Ball on 2015-04-26
* Just read your last post. Please mark as solved by following the second link in my signature.

---

### Post by michael-piziak on 2015-04-26
Yep, I was going to mark it as solved; however, I'm not sure that the problem in the original post was solved - as my solution was to wipe out Windows 8, to get Ubuntu to work, instead of keep it as a partition.

---

### Post by Bucky Ball on 2015-04-26
We don't have a 'resolved' option so that's the best you can do. Whatever issue you began with is now resolved, if not solved. ;)

---

