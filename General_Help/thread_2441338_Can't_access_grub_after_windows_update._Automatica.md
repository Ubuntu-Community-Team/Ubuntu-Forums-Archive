---
title: "Can't access grub after windows update. Automatically boots to Windows."
date: 2020-04-22
forum: General Help
---

### Post by jamesoreilly on 2020-04-22
Windows forced an update and I can no longer access grub and therefore can't access my Ubuntu partition. Computer automatically boots to Windows and I cannot find a boot option in the BIOS that opens grub when I reboot.

 I have tried using BootRepair with Ubuntu on a USB drive, but it has not worked and there is no boot option to access grub.

Here is a link to a pastebin with the BootRepair info report: [http://paste.ubuntu.com/p/JJkkrr6cJW/](http://paste.ubuntu.com/p/JJkkrr6cJW/)

I have a coursework due tomorrow which I need to do with Ubuntu so this timing is pretty unfortunate for me. Any help is greatly appreciated.

Cheers, 
James

---

### Post by oldfred on 2020-04-22
Have you looked in UEFI boot menu, it should show the ubuntu entry.
Report shows ubuntu entry from this command:
sudo efibootmgr -v

Some systems accept efibootmgr changing boot order. Others need you to change order in UEFI settings.

It also looks like Windows update turned fast start up back on. That is normal and will happen again.
You need to boot Windows and turn fast start up off again.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

It looks like you have nVidia but are using nouveau. With my old GT 620 card, I could not tell difference. But if newer nVidia card, you may get better performance from the nVidia proprietary driver.

#What is installed
dkms status

If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by jamesoreilly on 2020-04-22
Thank you for the detailed reply. I actually fixed the issue just now by changing the windows bootloader as the bootloader summary suggested. I had not seen this recommendation originally.

I have also turned off fast start up and I'll look into getting the nvidia proprietary drivers. Thanks again for the advice.

---

