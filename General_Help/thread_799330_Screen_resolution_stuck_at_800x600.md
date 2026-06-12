---
title: "Screen resolution stuck at 800x600"
date: 2008-05-18
forum: General Help
---

### Post by little8020 on 2008-05-18
I booted up my comp today at it was randomly stuck at 800X600. It has been fine before today but it just changed to 800X600 and it wont let me change it back in the screen resolution menu. I have a non-dedicated video card and release 8.04. Thanks for any help and if you need any other info I will try and give it.

---

### Post by paulnema on 2008-05-18
I'm having the same issue.  See thread:
[http://ubuntuforums.org/showthread.php?t=799282](http://ubuntuforums.org/showthread.php?t=799282)

What are you running?

---

### Post by little8020 on 2008-05-18
I tried what the guy said but didn't do any thing and as i said i use 8.04 with a non-dedicated vid card so i don't think it has to do with vid card or drivers.

---

### Post by diyowel on 2008-05-19
i also get the same problem. i use ubuntu via wubi stored in my external HD.  sometimes my screen is split into 4! how do i fix that?:(

---

### Post by vancouverite on 2008-05-19
Posting the contents of the file /etc/X11/xorg.conf might make this easier to solve.

You might try reconfiguring the x-window server from recovery mode.  To do this, reboot and select recovery mode from the grub boot loader.  Once you are at the command line (your desktop will not start) type (as root):

# dpkg-reconfigure xserver-xorg

This will take you through an guided setup for monitor, mouse and keyboard where you can mostly use the defaults.  When you get to the screen asking what resolutions your monitor/video card can handle, be sure your preferred resolution is selected.  This will write a new xorg.conf file which should load when you reboot.

Before rebooting type: "# shutdown now" to kill all processes.

Hope this helps,
Vancouverite

---

