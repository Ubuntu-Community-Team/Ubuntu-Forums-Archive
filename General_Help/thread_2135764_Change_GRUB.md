---
title: "Change GRUB"
date: 2013-04-15
forum: General Help
---

### Post by Binary-Synapse on 2013-04-15
Hello.

How can I change the text string from a GRUB entry in Ubuntu 12.04LTS (and make it permanent, even after a "update-grub")?

I remember that I used to edit file /etc/grub.d/10_linux
But I could be wrong. Is it still there?

Because currently I dont see the entry that I need to modify listed inside that file.

Help anyone?

Thank you

---

### Post by oldfred on 2013-04-15
As the grub versions have changed, the scripts have changed. As long as you look for the correct commands and not line numbers that may still work.

I prefer just to copy the boot entry into 40_custom and turn off os-prober. 
Or you can use grub customizer.

 New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

      
 Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

If that works then you can turn os-prober off to eliminate the search of system for other systems.
      
 In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

If you want entries you manually add first in menu, then copy 40_custom to  06_custom and edit 06_custom. You need the couple of lines at the top  of 40_custom so do not just create a new empty 06.

---

### Post by ajgreeny on 2013-04-15
Or if I understand you right, you can simply edit the contents shown in red between the single quote, or backtick marks in the line ```
GRUB_DISTRIBUTOR=`[COLOR=#ff0000]lsb_release -i -s 2> /dev/null || echo Debian[/COLOR]`
``` in /etc/default/grub to say whatever you want, enclose it in normal quotation marks, and that string, eg [COLOR=#ff0000]"[/COLOR][COLOR=#ff0000]My Ubuntu Precise- 12.04"[/COLOR] is what will show in the grub menu.

It may be easier to use grub-customiser, but it is not something I've ever used; I like to understand more about what I'm doing.  You can make your choice.

---

