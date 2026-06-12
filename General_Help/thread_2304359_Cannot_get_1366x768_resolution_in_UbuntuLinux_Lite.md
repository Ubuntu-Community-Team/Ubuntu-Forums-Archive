---
title: "Cannot get 1366x768 resolution in Ubuntu/Linux Lite"
date: 2015-11-26
forum: General Help
---

### Post by praji2 on 2015-11-26
Sir,
I am using Ubuntu & Linux Lite.
I cannot get 1366x768 resolution for display. The maximum is 1024x768.
Mine is Desktop PCs.  No graphic card only onboard graphic.
i3 system with 2GB memory. Wipro with foxcorn main board.
Duel boot with Windows 7.  No problem in Win7.
I have another system Lenovo E73 Desktop with win7+linux lite and it is working perfectly.

I have searched a lot and add the resolution with "xrandr" etc.etc.
But it only for the current session.  For permanent solution found something like "xorg.conf" etc., but in my system it is not found.

The same OS is working in one system and not in another system.

Please help me to solve this issue.
Thanks in advance.
PK

---

### Post by grahammechanical on 2015-11-26
> I have another system Lenovo E73 Desktop with win7+linux lite and it is working perfectly.

Are you comparing like with like? Comparing two machines with the same hardware and connected to the same make and model of monitor? What are the capabilities of both graphic adapter and monitor? For example, the xrandr command on my machine shows this:
> 
graham@sdb7-Dev:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080     60.05*+  60.00    59.94    50.00    23.97    60.00    50.04  
   1440x480      60.05  
   1280x1024     75.02  
   1280x800      84.88  
   1280x720      60.00    59.94    50.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       75.00    72.81    59.94    59.93  

There is no point in me trying to get 1366x768 because it is not in the list. So, what does the output from xrandr show on that machine?

I have also found that the connection from the motherboard to the monitor also makes a difference. Connecting with a VGA cable will limit the resolutions available when compared with connecting by DVI or HDMI.

With digital monitors Linux sets the screen resolution every time it loads not by reading the xorg.conf file but by interrogating the monitor's EDID (Extended Display Identification Data) chip and setting the optimum resolution from that. This is why when we install we do not need to set a screen resolution like we did in the old days with CRT monitors.

There is nothing stopping you creating your own xorg.conf

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

Regards.

---

### Post by praji2 on 2015-11-27
sir,
Thanks for reply.
I am not comparing, just want to fix my problem.
my xrandr result is

*campus@cadlab33:~$ xrandr*
*Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767*
*VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm*
*   1024x768       60.0**
*   800x600        60.3     56.2 *
*   848x480        60.0 *
*   640x480        59.9  *
*VIRTUAL1 disconnected (normal left inverted right x axis y axis)*


Let me try to create xorg.conf

---

### Post by ian-weisser on 2015-11-27
> **praji2 said:**
>  No graphic card only onboard graphic.

You are limited to whatever resolution the 'onboard graphic' supports.
You cannot add more options in software.
You can add more options in hardware...by adding a graphics or video card.

---

### Post by blm-ubunet on 2015-11-27
Post (as attachment) your Xorg log file
```
/var/log/Xorg.0.log
```
Rename the file with ".txt" on the end so the forums can cope.

Being limited to 1024x768 is a strong indicator that you're stuck on the VESA (non-KMS) driver.

---

### Post by praji2 on 2016-01-21
Sorry for the delay.
Still the problem is there.
I have attached the file.
Thanks

---

### Post by Bucky Ball on 2016-01-21
Are you running Ubuntu or Linux Lite??? Which distro are you attempting to do this in? Linux Lite is not Ubuntu. Please confirm.

If you are after support here, please attempt to fix your issue on Ubuntu. Switching between distros, particularly when posting output, can only be confusing. Thanks. ;)

---

### Post by praji2 on 2016-01-21
I have the same problem in both Ubuntu & linux lite.
But I need solution for any one.
Thanks

---

### Post by blm-ubunet on 2016-01-21
Your log file shows the intel driver is loaded/working.
Just seems to think the correct VGA1 video mode is 1024x768.
There is no information on EDID/DDC mode pool; could be caused by defaults for logging level.

---

