---
title: "Goes into Windows and not GNU Grub - what can I do?"
date: 2017-12-27
forum: General Help
---

### Post by tomsax on 2017-12-27
I have a HP laptop. A problem with installing ubuntu on it has been it tended to go straight to windows when booting up.  When this happens I need to press escape  and then F9 to get to this:

[ATTACH=CONFIG]277948[/ATTACH]

Then I choose ubuntu and get to here:

[ATTACH=CONFIG]277949[/ATTACH] 

Then I choose ubuntu (again).  

I know it is possible to do something and go straight to the second but I don't know what.  The odd thing it was going straight to the second until about a week ago.  Not sure why it changed but it may have been due to a windows update. 

If I can know how to put it right I can also do it on another laptop which also takes this long drawn out route to ubuntu.

Am using ubuntu 16.04.

Tom

---

### Post by oldfred on 2017-12-27
HP is not dual boot friendly. I violated the UEFI standard that says NOT to use description as part of boot. And of course only valid description is "Windows Boot Manager".
You can manually boot like you are.
Or you may be able to boot a hard drive entry or fallback type entry.

UEFI only boots external drives from /EFI/Boot/bootx64.efi. That then was added as a fallback entry for internal drives. You may already have in your ESP - efi system partition that file/folder, but file is just a copy of Windows .efi boot file.

If you run Boot-Repair it copies /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi to let you boot a hard drive entry.
Some also use rEFInd.

Before Boot-Repair did the copy, users manually copied files.
 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 
[https://ubuntuforums.org/showthread.php?t=2247186](https://ubuntuforums.org/showthread.php?t=2247186)

      
 Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

