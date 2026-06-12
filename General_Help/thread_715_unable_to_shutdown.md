---
title: "unable to shutdown"
date: 2004-10-15
forum: General Help
---

### Post by mbjbdc on 2004-10-15
hi
when i try to shutdown at the end the screen say power down 
but pc is still running . the only way to shut off is to turn off power to the unit

---

### Post by Robin Mehner on 2004-10-15
I had the same problem. I solved it with an bios update. Now it turn off automatically. Maybe this would work for you too.

---

### Post by HungSquirrel on 2004-10-15
I had that problem on another machine with another distro.  The problem was my BIOS doesn't like ACPI, but handles APM just fine.  I loaded the APM kernel modules and the thing shut down fine.  I don't know if it's the same for Ubuntu, but it could be.

---

### Post by mbjbdc on 2004-10-15
thanks for quick reply i will give it a try

---

### Post by mbjbdc on 2004-10-15
upgraded bios but no fix still no shutdown.
can somebody give me a simple how to enable apm in kernal
still kinda of a noob to linux

---

### Post by HungSquirrel on 2004-10-15
In console, *sudo modprobe apm*.  If it works, you won't see any messages displayed.  Then, shut down your machine.  If it shuts down correctly, that was probably the problem, so turn your computer back on, come back to this thread, and say so.  Then we can walk you through how to make it permanent.  8)   If not, then APM isn't the problem.

---

### Post by gabbman on 2004-10-15
I had to add "acpi=force" to the /boot/grub/menu.1st file in order to achieve the shut down.

---

### Post by mbjbdc on 2004-10-16
second bios update fixed shutdown problem
thanks

---

### Post by Geekboy on 2004-10-16
> In console, sudo modprobe apm.

HungSquirrel, this worked for me. :D  How do I make this permanent.  Thanks.  :)

---

### Post by HungSquirrel on 2004-10-16
Whoops, seems I'm unfamiliar with Debian startup scripts.  In Yoper, I added it to /etc/rc.d/init.d/local, but I'm not familiar with how Debian-like startup scripts work.  ubuntu-geek, wanna help?   :o

---

### Post by LongTooth on 2004-10-24
sudo modprobe apm worked for me. My machine did shut down properly. But I have no file named "/boot/grub/menu.1st". How can I make this permanent? Can someone help? Thanks.

---

### Post by NeiL on 2004-10-26
[QUOTE=Geekboy]HungSquirrel, this worked for me. :D  How do I make this permanent.  Thanks.  :)[/QUOTE]
Try to run "update-modules" as root or with sudo.
:)

---

### Post by sala on 2004-10-26
modprobe apm gives me this error:
FATAL: Error inserting apm (/lib/modules/2.6.8.1-3-k7/kernel/arch/i386/kernel/apm.ko): No such device

/lib/modules/2.6.8.1-3-k7/kernel/arch/i386/kernel/apm.ko is there, no file is missing

---

### Post by HungSquirrel on 2004-10-26
If *modprobe apm* does not work for you, you likely have a BIOS that doesn't support APM, which is why you got a "no such device" error.  In that case your problem is the ACPI bug in the 2.6.8.1 kernel that I believe is fixed in 2.6.9 .  Hopefully there will be a package for that kernel soon.

---

### Post by taygan on 2004-10-26
sudo modprobe apm worked great for my old Thinkpad 600, however it's not activating apm on reboot.  I used update-modules and the modules.conf has an apm section in it, but I still have to sudo modprobe apm everytime I start.

Any ideas?

---

### Post by jahLux on 2004-10-27
Halleu-Jah ! I figured it out..........FIRST...In the file description - "/boot/grub/menu.1st" -- the character after the "menu," is the lower-case letter L - not the digit 1!

Correct entry of the comand "sudo nano /boot/grub/menu.1st" in a terminal WILL bring up the required file. Carefully scroll down this file to the line :

"kernel /boot/vmlinuz-2.6.8.1-3-386 root=dev/hda_ ro quiet splash"

Add "acpi=force" to the end of the line - SAVE [Cntrl/X] and exit - then exit again! 

DONE !!

---

### Post by harryc on 2007-03-04
This is an old thread, but in case anyone with a Thinkpad 600e runs across this power down issue, this fixed it for me;

> POWER
The 600E has a few problems with how it does power. Since we kinda disabled ACPI before (implementation on the 600E is there, but buggy) we have to do the following to make sure Shutdown works. In a console window:

nano -w /etc/modprobe.d/power

add the following bit of code to the new file:

options apm power_off=1 realmode_power_off=1

And then EXIT from the file and reboot.
Reference - [http://www.blog.savant.be/linux/ubuntu-610-edgy-on-a-thinkpad-600e-2645-57u/15/](http://www.blog.savant.be/linux/ubuntu-610-edgy-on-a-thinkpad-600e-2645-57u/15/)

---

### Post by midijery on 2008-04-13
All yoor above mentioned solutions did not work, but I discovered a very quick and easy solution switch from KDM to GDM it worked for me. Your posts on this thread seem to be outdated and doesn't apply to the newer distros, perhaps this will help as a temporary fix until they get KDM fixed.
Jerry 
:)

---

