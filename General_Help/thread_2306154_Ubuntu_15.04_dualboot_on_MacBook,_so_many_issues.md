---
title: "Ubuntu 15.04 dualboot on MacBook, so many issues"
date: 2015-12-12
forum: General Help
---

### Post by reilemx on 2015-12-12
I have tried googling everywhere for about 2 hours now and have finally decided to post here.

Bit of background: I have been using a dualboot of Ubuntu 14.10 on a MacBook Air for a while but had this constant issue where if I suspended my computer (by either closing my laptop lid or selecting it from the top right drop down menu) and then brought it back. My screen would flicker to the login screen and then go black. Only a forced power off and restart would solve the problem. If by some magical chance my computer would successfully come back from a suspension which happened 1/10 times, then my screen brightness options were: complete darkness, or the light of a thousand suns.

So i thought upgrading to a newer version would help, oh how wrong I was. I upgraded to Ubuntu 15.04 by using the recommended steps on the 'official' Ubuntu website, and the upgrading showed no signs of error. I then restarted my computer and instantly regretted I had not made a bigger backup.

The issues:

- Suspension problem is still not fixed. Plus, whenever I enter Ubuntu my screen brightness and keyboard brightness are set to max.

- Trackpad/mouse can click, and the clicks are registered but the pointer refuses to move, rendering the OS pretty much unusable. I have tried following this guide: [https://help.ubuntu.com/stable/ubuntu-help/mouse-problem-notmoving.html](https://help.ubuntu.com/stable/ubuntu-help/mouse-problem-notmoving.html) and this guide: [http://askubuntu.com/questions/595530/ubuntu-14-04-mouse-can-click-but-cannot-move](http://askubuntu.com/questions/595530/ubuntu-14-04-mouse-can-click-but-cannot-move) and so, so many more. This is a built in track pad, I have lost count of how many "sudo apt-get install 'xxx'" I have performed just to get "Unable to locate package...". I've even tried a full apt-get update and dist-upgrade, none of these things have done anything. Also tried a bunch of other command which I am unsure of what exactly they do like "sudo modprobe -r psmouse" and "sudo modprobe psmouse proto=imps" both did absolutely nothing (not even any sort of confirmation or error in terminal).

[SIZE=2][FIXED] -rEFINd is dead in the water. Every time I start up my computer it goes straight to Ubuntu, unless I hold in my alt (option) key then I can choose Macintosh HD as boot, but in this menu Ubuntu is not displayed. I'm not even sure where to begin with this one. I guess I should have assumed that rEFINd would crap out when updating Ubuntu, but I installed rEFINd ages ago, and have no idea how to uninstall/reinstall or fix it. I don't even know where it's installed at this point.[/SIZE]

Any ideas or solutions to any one of these problems would be greatly appreciated. Keep in mind that if I need to put any debug info on this site that I will have to do this with keyboard only, and shortcuts that you can recommend to make that happen will be greatly appreciated. I'm currently typing this on a second windows laptop.

UPDATES:

Still no fix to the suspension issue.

I have tried plugging in a USB wireless mouse from Logitech and that  DOES work. So my pointer can move, there just seems to just be no  connection between my MacBook trackpad/touchpad and Ubuntu. Google still  has nothing to offer about this though,

A simple rEFInd install in my OSX partition fixed my rEFInd problem.

---

