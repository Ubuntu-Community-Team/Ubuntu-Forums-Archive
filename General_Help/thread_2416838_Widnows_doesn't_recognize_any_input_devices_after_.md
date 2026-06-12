---
title: "Widnows doesn't recognize any input devices after dual boot"
date: 2019-04-16
forum: General Help
---

### Post by i3abghany on 2019-04-16
I have successfully installed ubuntu dual boot with windows 10. After I got into ubuntu, I restarted my laptop and it went straight to windows without showing GRUB. I searched for a solution and everyone said that I had to turn off fast startup, I diaabled it using a .bat file which was on tenforums as a guy on youtube did.
I then tried to restart my computer, it didn't show grub either. Also, the computer froze and my mouse and keyboard weren't responding, and the sound icon in the start bar was showing an x which i think means that the sound driver is not being identified also. Can you please help?
My laptop is Lenovo Ideapad520

---

### Post by oldfred on 2019-04-16
Best to follow directions on turning off fast start up, unless you really understand what someone's script is doing.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

       
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
        
 Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208)

---

### Post by i3abghany on 2019-04-16
I did what's in the first link, I managed to get the GRUB interface in the start of the boot and linux works well. But windows is frozen, and only the brightness buttons on keyboard are working, everything else is not recognized.

---

### Post by jdeca57 on 2019-04-16
> **i3abghany said:**
> ...But windows is frozen, and only the brightness buttons on keyboard are working, everything else is not recognized.
You can always restore Windows. Simply download the iso of your version and boot from it. Activation is not an issue if the hardware is the same. The problem is that it may delete the Ubuntu boot (grub). If that were the case you have a second chance at installing grub.

---

### Post by oldfred on 2019-04-16
Are you booting Windows from grub or directly from UEFI boot menu?
Best to see is UEFI boot menu works as grub only boots working Windows which means Windows cannot be hibernated nor need chkdsk or perhaps other issues.
Not quite sure what difference it is when direct booting vs. grub, but there is something.

---

