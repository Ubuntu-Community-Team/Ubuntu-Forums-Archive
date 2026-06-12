---
title: "boot into blank screen"
date: 2021-12-13
forum: General Help
---

### Post by monkeybrain20122 on 2021-12-13
Hi, This suddenly happened. After waking up from suspense the gui doesn't appear, after rebooting the login screen is blank but I can type my password and login (I can hear the login sound) I could neither boot into recovery mode nor switched to tty, both gives just blank black screen.

However, everything works if I connect the laptop to an external monitor and with the laptop own dispiay( not the external monitor) I can also boot up from a live usb and I can access BIOS/UEFI settings with no problem.

It is a system 76 laptop with Nvidia GTX1070, The last driver update was like a week ago and I had rebooted and woke up from suspense many times with no issue. This just happened (also same issue if I choose integrated  graphics, i.e intel from uefi settings so it doesn't look like gpu issue, and as I said it works on a second monitor)

Help is greatly appreciated.

---

### Post by KBar on 2021-12-13
I'd suggest checking what packages were upgraded. Also, what's in the */usr/lib/systemd/system-sleep* directory?

---

### Post by monkeybrain20122 on 2021-12-14
bump

---

### Post by #&amp;thj^% on 2021-12-14
Maybe you've seen or read this: [https://support.system76.com/articles/login-loop-pop/](https://support.system76.com/articles/login-loop-pop/)

---

### Post by monkeybrain20122 on 2021-12-14
> **1fallen said:**
> Maybe you've seen or read this: [https://support.system76.com/articles/login-loop-pop/](https://support.system76.com/articles/login-loop-pop/)

Hi, I did. But I could not switch to tty. Ctrl+alt+F5 still show only shows a blank screen even though I could tell screen was refreshed (so key combo is correct)

---

### Post by #&amp;thj^% on 2021-12-14
Can you hit a tty with the second/external monitor?

---

### Post by monkeybrain20122 on 2021-12-14
Yes. On the second Mon everything works. But I don't have one now, is there a way to trouble shoot it with a live usb?

---

### Post by #&amp;thj^% on 2021-12-14
Intel or AMD for second graphics?

---

### Post by monkeybrain20122 on 2021-12-14
You mean second gpu? It is intel. I could switch to integrated from discrete (Nvidia) from bios, but same result (blank screen, no tty, but worked in second mon)

---

### Post by #&amp;thj^% on 2021-12-14
GPU Graphics Processing Unit
I would try to add another user to see if any difference is noticed.

---

### Post by monkeybrain20122 on 2021-12-14
since I cannot even get into recovery mode (blank screen), I am not sure if it has anything to do with the user's $HOME config.

---

### Post by #&amp;thj^% on 2021-12-14
Up to you.
One other suggestion to ponder.
Remove the NVIDIA driver, run the following:
```

sudo apt purge ~nnvidia
sudo apt autoremove
sudo apt clean
```
Anyway Good Luck

---

### Post by monkeybrain20122 on 2021-12-16
> **1fallen said:**
> Up to you.
One other suggestion to ponder.
Remove the NVIDIA driver, run the following:
```

sudo apt purge ~nnvidia
sudo apt autoremove
sudo apt clean
```
Anyway Good Luck

Hi, removing the Nvidia driver does work, but reinstall the driver or installing a different driver (nvidia-470 -> 495) the problem returns.

---

### Post by tea for one on 2021-12-16
There is a similar thread here [https://ubuntuforums.org/showthread.php?t=2469719](https://ubuntuforums.org/showthread.php?t=2469719)

The OP has a [COLOR="#0000FF"]2020 System76 Gazelle with Nvidia[/COLOR] and, although the solution was not published, it appeared that the hardware vendor supplied the fix.

Also, there is a huge sticky thread [https://ubuntuforums.org/showthread.php?t=1743535](https://ubuntuforums.org/showthread.php?t=1743535)

I wish that I could offer more concrete assistance but I've little experience with Nvidia.

---

### Post by KBar on 2021-12-16
Purge all of the drivers including nouveau and reinstall it with:
```
ubuntu-drivers autoinstall
```

---

### Post by monkeybrain20122 on 2021-12-16
> **tea for one said:**
> There is a similar thread here [https://ubuntuforums.org/showthread.php?t=2469719](https://ubuntuforums.org/showthread.php?t=2469719)

The OP has a [COLOR=#0000FF]2020 System76 Gazelle with Nvidia[/COLOR] and, although the solution was not published, it appeared that the hardware vendor supplied the fix.


It is not the same problem. I can boot, only no graphic in built in display with the proprietary Nvidia driver,--but graphic shows on external monitor, and built in display works without the proprietary driver.

so it looks like somehow the built in display cannot connect to the proprietary graphic driver.

---

### Post by Skaperen on 2021-12-16
just following the original description, it sounds like the problem is in state files for the display manager, probably **lightdm**.  unfortunately, i have not worked with it any and have no clue how to convince it that it should not be trying to resume from suspend (which it seems to be doing with an X driver that doesn't know the right way to do that for **X**).  i only know its role, not how it is designed.

i suggest that you spend any free time backing up your data, like /home and your settings.  trying to fix this could make things worse (like unbootable) and you might need to re-install (which is the hardcore extreme way to fix most software problems).  by having the backup already done, you can feel safer doing extreme try-this tests.  a 2nd backup is always a plus.  3 for the paranoid.  4 if you also are OCD.

---

### Post by monkeybrain20122 on 2021-12-17
> **Skaperen said:**
> just following the original description, it sounds like the problem is in state files for the display manager, probably **lightdm**.  unfortunately, i have not worked with it any and have no clue how to convince it that it should not be trying to resume from suspend (which it seems to be doing with an X driver that doesn't know the right way to do that for **X**).  i only know its role, not how it is designed.

i suggest that you spend any free time backing up your data, like /home and your settings.  trying to fix this could make things worse (like unbootable) and you might need to re-install (which is the hardcore extreme way to fix most software problems).  by having the backup already done, you can feel safer doing extreme try-this tests.  a 2nd backup is always a plus.  3 for the paranoid.  4 if you also are OCD.

I won't mind reinstalling but I want to make sure that it is not a hardware issue first. Not sure how to go about that though.

---

### Post by monkeybrain20122 on 2021-12-17
So the symptoms appear to match answer2 from [https://askubuntu.com/questions/744419/blank-screen-after-nvidia-install](https://askubuntu.com/questions/744419/blank-screen-after-nvidia-install)

However I don't have a /etc/X11/xorg.conf. Where is this info stored for Ubuntu 20.04? 

Thanks

---

### Post by gsahli on 2021-12-18
You create your own xorg.conf, because it isn't required for well-behaved hardware. It is useful for specifying the driver if a working driver for an older model works, for example. Or some option works...
You can use a utility to make an xorg.conf for you, like in the old days. but these utilities may be deprecated and unavailable...
[https://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file#:~:text=Generate%20new%20xorg.conf%20file:%20sudo%20X%20-configure%20This,will%20create%20xorg.conf.new%20file%20in%20your%20current%20directory](https://askubuntu.com/questions/217758/how-to-make-an-xorg-conf-file#:~:text=Generate%20new%20xorg.conf%20file:%20sudo%20X%20-configure%20This,will%20create%20xorg.conf.new%20file%20in%20your%20current%20directory).

---

### Post by monkeybrain20122 on 2021-12-20
bump

---

### Post by Skaperen on 2021-12-20
> **monkeybrain20122 said:**
> I won't mind reinstalling but I want to make sure that it is not a hardware issue first. Not sure how to go about that though.

boot up a bootable ISO (on a CD or flash memory stick) and bring up Ubuntu Live that way.  if you get the same blank screen then you might have a hardware problem.  if it comes up into Live mode, which will be graphical, then your hardware looks good.  that Live mode is also a good place to access your host files to fix them.

---

### Post by monkeybrain20122 on 2021-12-20
> **Skaperen said:**
> boot up a bootable ISO (on a CD or flash memory stick) and bring up Ubuntu Live that way.  if you get the same blank screen then you might have a hardware problem.  if it comes up into Live mode, which will be graphical, then your hardware looks good.  that Live mode is also a good place to access your host files to fix them.

Ubuntu live usb only boots with nomodeset (safe graphic mode) but adding nomodeset in my internal installation's grub conf doesn't work. like I said, built in display works if removed Nvidia driver. So it is something about how Nvidia driver and X connect.

---

### Post by monkeybrain20122 on 2021-12-21
So I borrowed an external  montor and booted up the gui

```
xrandr
Screen 0: minimum 8 x 8, current 2560 x 1080, maximum 32767 x 32767
HDMI-0 connected primary 1920x1080+640+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1400x1050     59.98  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00  
   1152x864      75.00
   1024x768      75.03    60.00  
   800x600       75.00    60.32    56.25  
   640x480       75.00    59.94  
DP-0 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480       59.94*+
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis) 
```

DP-0 is the built in display (which is blank)


Without the Nvidia driver,  the built in displau appears with nomodeset.

---

### Post by monkeybrain20122 on 2021-12-21
I restored from an old image from Nov 13 but still am having the same problem. The problem didn't exist when I created the image.

---

### Post by monkeybrain20122 on 2021-12-22
So I did a clean install and encounter the same issue. Without installing Nvidia driver, built in display works. After installing the Nvidia driver, only the external display shows even though the built in monitor is detected, but with 640 x 480 resolution, should be 1920x1080. You can see the built in display appears as a small box next to the main window in the external monitor.

---

### Post by monkeybrain20122 on 2021-12-22
```
xrandr --listmonitors
Monitors: 2
 0: +*HDMI-0 1920/521x1080/293+0+0  HDMI-0
 1: +DP-0 640/169x480/127+1920+0  DP-0
bernard@netramark:~$ xrandr --listactivemonitors
Monitors: 2
 0: +*HDMI-0 1920/521x1080/293+0+0  HDMI-0
 1: +DP-0 640/169x480/127+1920+0  DP-0
```

This is from the external monitor. The built in monitor is detected and list as "active" but with very low resolution and  its display is tugged to a corner as in the external monitor as shown in the screenshot above.

---

### Post by monkeybrain20122 on 2021-12-26
bump

---

### Post by monkeybrain20122 on 2021-12-30
Bump!

---

### Post by monkeybrain20122 on 2022-01-04
bump

---

### Post by monkeybrain20122 on 2022-01-06
bump

---

### Post by &amp;KyT$0P# on 2022-01-06
> **monkeybrain20122 said:**
> I restored from an old image from Nov 13 but still am having the same problem. The problem didn't exist when I created the image.

This sounds to me it's likely deeper than any OS/driver level issue.

> **monkeybrain20122 said:**
> It is a system 76 laptop 

Have you asked System76 support about this?

---

