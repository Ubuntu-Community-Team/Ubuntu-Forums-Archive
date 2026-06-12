---
title: "Command line on normal mode boot normal?"
date: 2008-05-18
forum: General Help
---

### Post by otto888 on 2008-05-18
When I installed ubuntu 8.04 via Wubi,when I boot it in NORMAL mode,all I get is a command line.:confused: and I can't exit or anything!(Without pulling the plug of corse)can anyone tell me how to fix this? The ubuntu loading bar shows for about 5 seconds and thens goes to the command line.

---

### Post by tamoneya on 2008-05-18
first of all rebooting can be done with: ```
sudo reboot
```.  As for how to get a GUI you should try ```
startx
```

---

### Post by chrisccoulson on 2008-05-18
Do you get any error messages on the screen? Is the command prompt giving you the opportunity to log in with your usual credentials, or is it just a root shell? If it is just a root shell, then it's likely to be Busybox, and you're there because something is broken (like not being able to find the root filesystem etc)

---

### Post by otto888 on 2008-05-18
> **chrisccoulson said:**
> Do you get any error messages on the screen? Is the command prompt giving you the opportunity to log in with your usual credentials, or is it just a root shell?

I think its a root shell. it kinda looks like DOS.

---

### Post by ibuclaw on 2008-05-18
When you say command line, do you mean a login prompt or a shell?

To help you distinguish between the two.
A shell will look like this:
[PHP]name@ubuntu:~$ [/PHP]
If you are root, it will look like this (notice the hash "#" symbol):
[PHP]name@ubuntu:~# [/PHP]
A login prompt will look like this:
[PHP]ubuntu login:[/PHP]

If you see something else, please specify.

Regards
Iain

---

### Post by otto888 on 2008-05-18
its none of those...I'll get a pic once I reinstall ubuntu.

---

### Post by otto888 on 2008-05-18
heres the pic.[IMG]http://img220.imageshack.us/img220/6657/img0503rz0.jpg[/IMG]

---

### Post by otto888 on 2008-05-18
Sorry but...bump! has anyone have ANY idea whats going on? none of the command lines above worked!

---

### Post by ibuclaw on 2008-05-19
Hmm... It's been a while since I last saw that shell.
Busybox is the emergency shell for when the main kernel can't boot, due to not finding the disk or some other error, is it not?

When Ubuntu boots, are you asked whether or not you want the GRUB boot menu to show?

If so, press "**Esc**" to view the menu/stop the countdown.

Make sure that the first option is being highlighted, then press the "**E**" key to go into the edit mode.

Take note of the "**root (hd0,0)**" option (what the numbers are after the "hd" part), as you'll need to know this in a moment.

Highlight the "kernel" option (should be line two) and then press "**E**" again.

You should now be in the edit mode of the kernel line. Press the "Left" and "Right" Arrow keys to view it all.

Now, locate the command "root=UUID=5658885-s43r-3df43-sf43r", the UUID number is just jargon, don't expect it to be the same as mine.
Then delete it all (Don't remove anything else. All other commands are delimited by spaces).
Then type in "**root=/dev/sda1**" in it's place.

Now, the above may not be correct for what you have to type in, that is why I asked for you to take notice of the "hd0,0" display.

Basically, the first digit you replace with its alphabet equivalent, and the second digit you add by 1.

ie:
hd0,0 = a1
hd2,0 = c1
hd1,4 = b5

To make sure that you are still following me, if my root hd was showing "root(hd1,4)"
Then I would replace the "root=UUID=***" with "**root=/dev/sdb5**"

Regards
Iain

---

