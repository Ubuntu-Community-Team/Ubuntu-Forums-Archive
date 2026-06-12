---
title: "Can't Access Grub after Windows Reinstall: already tried boot-repair, bcdedit"
date: 2019-02-04
forum: General Help
---

### Post by rguthrie14 on 2019-02-04
I've been dual-booting Windows 10 and Ubuntu 16.04 on my Acer Aspire ES 15 and had to reinstall Windows. Boot repair says it was successful and I tried
  
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

Here's the link to my boot repair summary [http://paste.ubuntu.com/p/727VTYYzRx/](http://paste.ubuntu.com/p/727VTYYzRx/)

I'm sorry this is a commonly asked question but I've been spending hours and hours watching videos and scrolling through forums and I can't get it to work.

---

### Post by oldfred on 2019-02-04
You need to first turn off Windows fast start up which sets hibernation flag.
And you need to enable "trust" on your Ubuntu/grub .efi boot files.
If you have not updated UEFI from Acer, you need to also do that first.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
    
       Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
    
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by rguthrie14 on 2019-02-04
Turning off fast start and enabling trust did the trick. Thank you so much! You've saved me a lot of pain.

---

