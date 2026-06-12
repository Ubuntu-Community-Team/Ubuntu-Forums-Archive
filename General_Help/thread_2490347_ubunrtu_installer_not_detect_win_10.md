---
title: "ubunrtu installer not detect win 10"
date: 2023-08-31
forum: General Help
---

### Post by omid2s on 2023-08-31
[COLOR=#000000][SIZE=3]hi
I create bootable usb flash memory with Ventoy and copy "[/SIZE][/COLOR][COLOR=#000000][SIZE=3]ubuntu-23.04-desktop-amd64" [/SIZE][/COLOR][COLOR=#000000][SIZE=3]into it.
my laptop processor is AMD APU A6.
every things is ok and go on ubuntu installer ....select languge and...
but not show "Install ubuntu along side the window".

I disable fast boot and in CMD disable hibernation.
SATA mode is AHCI.
[/SIZE][FONT=sans] [FONT=arial][SIZE=3]Launch CSM is enable.[/SIZE][/FONT][/FONT][/COLOR][SIZE=3][COLOR=#000000][SIZE=3]
[/SIZE]
but still donot show "install alonge side...."[/COLOR]
my partitions:

[/SIZE][IMG]https://s6.uupload.ir/files/1_ynt.jpg[/IMG]






Bios setting:

[https://s6.uupload.ir/files/2_5jcy.jpg](https://s6.uupload.ir/files/2_5jcy.jpg)


[https://s6.uupload.ir/files/3_r70u.jpg](https://s6.uupload.ir/files/3_r70u.jpg)


[https://s6.uupload.ir/files/4_b4n.jpg](https://s6.uupload.ir/files/4_b4n.jpg)


[https://s6.uupload.ir/files/5_h502.jpg](https://s6.uupload.ir/files/5_h502.jpg)

---

### Post by QIII on 2023-08-31
I believe that option is now called "Do something else".

Do you see that option?

---

### Post by omid2s on 2023-08-31
[SIZE=3]No
only exist two options

One option is format entire ssd or hard.
another is " manual partition"[/SIZE]

---

### Post by yancek on 2023-08-31
> [COLOR=#000000][SIZE=3][/SIZE][FONT=sans] [FONT=arial][SIZE=3]Launch CSM is enable.[/SIZE][/FONT][/FONT][/COLOR][SIZE=3][COLOR=#000000][SIZE=3]
[/SIZE][/COLOR][/SIZE] 

Disable that under your boot options as you will need to install Ubuntu in EFI mode as your windows is EFI.  If they are not both EFI, Grub won't boot windows.

I don't know why the install alongside doesn't show.  There should be an option for Manual partitioning as shown at the Ubuntu site at the link below.  You show unallocated space on the first windows drive so you should be able to install there.  

[https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-type-of-installation)

---

### Post by grahammechanical on 2023-08-31
It is my guess that you do not have the Windows operating system on that machine. What partition is Windows on? I cannot see any reference to an operating system. Without an operating system the installer cannot offer an install alongside option.

Regards

---

### Post by oldfred on 2023-09-01
Double check that Windows fast startup/hibernation is off. Windows turns it back on with updates which may occur if you boot back into Windows.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

