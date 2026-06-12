---
title: "USB mouse freezes for several seconds"
date: 2008-01-13
forum: General Help
---

### Post by scuba_steve_va on 2008-01-13
Hi.  I have read countless threads here (and elsewhere), but none have helped..so here goes:

Running Ubuntu 7.10...fresh install.

Using a USB optical mouse.


The problem:  The mouse cursor freezes for a couple of seconds randomly...and then it then starts to work again...and this happens quite frequently.  It often also slightly delays initial movement when it is not freezing...and IT IS MADDENING.

What the heck?  Accurate mouse movement is pretty much absolutely required for this OS to be a viable desktop OS.  I am trying to install it on someone's box as a safe means to surf and check email, but I am about to give up and tell them that Ubuntu is not ready for prime time.

Any advice?


BTW, I disabled powernowd...but the issue is still there.

---

### Post by erpo on 2008-01-14
This used to be a huge problem on Linux. It would happen when Linux decided that X should be paused to run a process that Linux felt was more important.

Open up a console and run top. Look for programs that use all of the CPU time even when the system should be idle.

---

### Post by scuba_steve_va on 2008-01-14
Thanks much for the reply, but I already had tried that before posting...and my (hyperthreaded) CPU is mostly idle and I do not see any culprit jump to the top of the list when the freezes occur.  It seems to me that it is more of a mouse driver or USB bus issue...but I have already switched the driver to evdev with no improvement.



BTW, I also should have mentioned that I have had this same mouse connected to this same PC with Windows XP and there were absolutely no issues at all.

---

### Post by frefactory on 2008-01-16
[FONT="Verdana"]I had a similar problem. Happened only in Linux distros, not on Win.  It was combined with difficulty to type. Characters would not appear at all, or appear multiple times and way too late. 

I solved the problem, by either installing a new "Vanilla Kernel" (you can find the tuts here in the forum), or by disabling ACPI in Grub.

edit /boot/grub/menu.lst

add **[COLOR="DarkRed"]acip=off[/COLOR]** in the line that boots linux. 

For example, in my menu.lst you can find : [/FONT]
[INDENT][FONT="Fixedsys"]
title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=f16cecde-0d45-46dd-a32d-cf9dbd4a161f [COLOR="DarkRed"]acpi=off[/COLOR] ro quiet splash locale=de_DE
initrd		/boot/initrd.img-2.6.22-14-386
quiet[/FONT][/INDENT]

[FONT="Verdana"]Reboot and give it a shot. I don't know if you are having the same bug, but this could be  a workaround.
By turning ACPI off, you do have a slight loss in performance, but use it till a new and better kernel is released.

cheers! [/FONT]

---

