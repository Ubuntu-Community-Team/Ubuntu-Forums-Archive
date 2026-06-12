---
title: "Ubuntu stalls on shutdown"
date: 2007-07-08
forum: General Help
---

### Post by AhrenBa on 2007-07-08
Hey guys,

I have Ubuntu 7.04 Feisty Fawn and am having a problem when trying to shutdown machine.

I go to the top right corner, click the power icon, and hit "shut down". It'll start to work, and once the process hits the Ubuntu logo screen with the loading bar directly below, it stalls and doesn't progress. Instead it just stays on this screen (and won't shut down).

What could be causing this and what are some solutions?

---

### Post by pmg on 2007-07-08
Try going to the tty console (hold down "ctrl" and "alt" and press **F1**) and see what messages are displayed.  You might also find something helpful in one of the log files in /var/log.  I would start by looking for messages with timestamps that match your shutdown time in "daemon.log" (or "daemon.log.0"), but you may also find something helpful in "messages" or "syslog".

---

### Post by az on 2007-07-08
> **AhrenBa said:**
> Hey guys,

I have Ubuntu 7.04 Feisty Fawn and am having a problem when trying to shutdown machine.

I go to the top right corner, click the power icon, and hit "shut down". It'll start to work, and once the process hits the Ubuntu logo screen with the loading bar directly below, it stalls and doesn't progress. Instead it just stays on this screen (and won't shut down).

What could be causing this and what are some solutions?

How old is the machine and what power management does it use? (you may need to look in the BIOS setup to tell)

---

### Post by AhrenBa on 2007-07-08
> **pmg said:**
> Try going to the tty console (hold down "ctrl" and "alt" and press **F1**) and see what messages are displayed.  You might also find something helpful in one of the log files in /var/log.  I would start by looking for messages with timestamps that match your shutdown time in "daemon.log" (or "daemon.log.0"), but you may also find something helpful in "messages" or "syslog".


I will check this out and post back what the results are. How do you exit out of the tty console?

> How old is the machine and what power management does it use? (you may need to look in the BIOS setup to tell)

The machine is from 2000 (eMachines 500is with some upgrades). I don't think I have any power management setup for it, but what should I be looking for that could cause problems (in power management.) Thanks!

---

### Post by az on 2007-07-09
> **AhrenBa said:**
> 
The machine is from 2000 (eMachines 500is with some upgrades). I don't think I have any power management setup for it, but what should I be looking for that could cause problems (in power management.) Thanks!


In the BIOS setup, can you select between APM and ACPI?  Try either.

Also, run this and post the file:

dmesg > file

Dmesg will display the kernel messages as you boot.  That command will dump the text into the file named "file".

---

### Post by pmg on 2007-07-10
> **AhrenBa said:**
> How do you exit out of the tty console?

The Xserver runs on tty 7, so ctrl-alt-F7 moves you back to the graphics Xserver display.

---

### Post by AhrenBa on 2007-07-10
> **az said:**
> In the BIOS setup, can you select between APM and ACPI?  Try either.

Also, run this and post the file:

dmesg > file

Dmesg will display the kernel messages as you boot.  That command will dump the text into the file named "file".

Where do I run the "dmesg"? Thanks.

> The Xserver runs on tty 7, so ctrl-alt-F7 moves you back to the graphics Xserver display.

Ok, thanks. Do I need to type in anything to see the messages? If not, here is what I currently see in the TTY console:

Starting Up.....
Please Wait....
kinit: name_to_dev_t(/dev/hda5) = hda5 (3,5)
kinit: trying to resume from /dev/hda5
kinit: No resume image, doing normal boot

---

### Post by pmg on 2007-07-11
> **AhrenBa said:**
> 
Ok, thanks. Do I need to type in anything to see the messages? If not, here is what I currently see in the TTY console:

Starting Up.....
Please Wait....
kinit: name_to_dev_t(/dev/hda5) = hda5 (3,5)
kinit: trying to resume from /dev/hda5
kinit: No resume image, doing normal boot

That is strange.  Those messages are from the beginning of boot up.  I would at least expect to see a login prompt after them.  Did you hit ctrl-alt-F1 right after clicking the shutdown button or did you wait until it seemed to hang?  Try hitting it right away.

I assume you cannot login or run arbitrary commands at the point where it's hung.  dmesg is a command to run on a tty or terminal emulator (like in an xterm window) but it doesn't sound like you can run it at the point where you get the hang.

Did you look in the log files for any indication of what it was doing, or what it had just done, at the point where it hangs?

---

### Post by GerryB on 2007-07-11
> **AhrenBa said:**
> Hey guys,

I have Ubuntu 7.04 Feisty Fawn and am having a problem when trying to shutdown machine.

I go to the top right corner, click the power icon, and hit "shut down". It'll start to work, and once the process hits the Ubuntu logo screen with the loading bar directly below, it stalls and doesn't progress. Instead it just stays on this screen (and won't shut down).

What could be causing this and what are some solutions?

In older systems you see a message at boot up that says ACPI forced (cutoff date before 2000 or such).
If this is the case, this thread might solve your problem. It solved mine.
[http://ubuntuforums.org/showthread.php?t=359190](http://ubuntuforums.org/showthread.php?t=359190)

---

### Post by az on 2007-07-11
> **AhrenBa said:**
> Where do I run the "dmesg"? Thanks.




Applications, accessories, terminal

---

