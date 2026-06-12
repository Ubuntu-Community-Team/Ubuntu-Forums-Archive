---
title: "Install failing please help"
date: 2013-08-02
forum: General Help
---

### Post by verti89 on 2013-08-02
I am giving Ubuntu a go for the first time as an OS for a media server. A few weeks ago I installed Ubuntu server 12.04 and it went fine on the first pass. Then I got busy and hadnt gotten to mess with the machine in a few weeks until a couple nights ago. When I booted it up all I got was a pink screen with a text box at the bottom that didnt seem to do anything. After various attempts to get it repaired I eventually gave up and wiped the HDDs. I the  was able to install Ubuntu desktop 13.04 and it said the installation was completed successfully with no errors. However upon reboot I got a "error: attempt to read or write outside of the disk 'hd0'" and a grub repair prompt. I used the live boot DVD I had made to install the OS and did the "try" option which allowed me to install and run boot-repair. Again this completed successfully but when I rebooted I got the same error. This is the URL I was given by the boot repair: [http://paste.ubuntu.com/5939233](http://paste.ubuntu.com/5939233)

Please help!

---

### Post by ing.tani on 2013-08-02
It seems you have a 3TB partition.
[COLOR=#000000]Install gdisk. (You can get it from synaptic or [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/))
[/COLOR]Then run "sudo gdisk /dev/sda"
Perhaps you should also have a bios_grub partition.

---

