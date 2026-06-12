---
title: "Acer Aspire no back light"
date: 2013-01-06
forum: General Help
---

### Post by mawil1013 on 2013-01-06
I found an answer to this (Acer Aspire has no back light) but it is for Ubuntu version 10. Plus when I connected a monitor to the laptop, it worked fine but the laptop monitor itself won't work.

I've installed Ubuntu 12.1, same situation. The laptop back light doesn't run. I have no success using the 'Fn+*< nor >*' keys to increase or decrease back light.

I entered, Ctri, Alt, T in order to bring up the Terminal, which worked,

then entered, gksudo gedit /etc/default/grub, which brought up grub file,

then added/entered; 
GRUB_CMDLINELINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

Now here is where I'm not sure what to do next, in the old post it said to enter this,

sudo update-gru, They don't say where, I assumed after the paragraph of the code? then hit enter? I see a Save button at the top also on 12.1.

So, am I correct to assume that after I make the additions to the code that I should scroll to the end of all the code, then enter the finial, sudo update-grub, then hit enter??

I'm asking this after having made an attempt to no avail, just messed it so the monitor I connected to the laptop didn't even work.

---

### Post by Jay MC on 2013-01-06
sudo update-grub looks like a terminal command, so I'd try entering it in terminal.  Like you did with the original commands that brought up the text file for you to edit.  Have you got a link to the fix that you're following...?

---

### Post by mawil1013 on 2013-01-06
> **Jay MC said:**
> sudo update-grub looks like a terminal command, so I'd try entering it in terminal.  Like you did with the original commands that brought up the text file for you to edit.  Have you got a link to the fix that you're following...?

Yes, here it is, [http://ubuntuforums.org/showthread.php?t=1781055](http://ubuntuforums.org/showthread.php?t=1781055)

I'm actually using Ubuntu 12.1 from my laptop right now, but only by using the monitor I've plugged into it, the laptop top screen backlight is still defunct, I can see Ubuntu on ot if I shine a flashlight onto it. 

It's sooo close to being functional, if I can just get past this monitor thing. Also, I rebooted and went back in and do see the command changes I made are still there, as well as at the end of the paragraph is the, command, sudo update-grub, is that supposed to still be there??

---

