---
title: "Can' change brightness Ubuntu 12.4 LTS @Toz"
date: 2013-11-05
forum: General Help
---

### Post by jeffhaddow on 2013-11-05
Hello Toz

Below are the details of my system that you've asked others:

Boot parmeter line:
```
jeff@lap-jeff:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-42-generic root=UUID=8ee21a60-1c0e-44b7-a110-bd182cde7b23 ro quiet splash


```

Video card and drivers:
```
jeff@lap-jeff:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device 6500
    Kernel driver in use: i915


```

Backlight interface  values:
```
jeff@lap-jeff:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
0
0
10
/sys/class/backlight/intel_backlight
1390
1390
1390


```

xorg log file:
```
jeff@lap-jeff:~$ pastebinit /var/log/Xorg.0.log
http://paste.ubuntu.com/6366483/


```


I cannot currently change the brightness from the max that it is set at either via keyboard shortcuts or ubunru software.
Can you suggest a solution for me?

All the best
Jeff

---

### Post by Toz on 2013-11-05
Can you try the **acpi_backlight=vendor** kernel parameter? For information on how to try it out, follow the "Temporarily Add a Kernel Boot Parameter for Testing" section from the [KernelBootParameters]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") wiki.

Once you've rebooted with the kernel parameter, check to see if brightness works and post back the same results as per your initial post.

If it works, we can make it permanent.

---

### Post by jeffhaddow on 2013-11-05
Hello Toz

It didn't chnge the brightness control not working 

Here's the tests again:
```
jeff@lap-jeff:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-42-generic root=UUID=8ee21a60-1c0e-44b7-a110-bd182cde7b23 ro quiet splash
jeff@lap-jeff:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device 6500
    Kernel driver in use: i915
jeff@lap-jeff:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
5
5
10
/sys/class/backlight/intel_backlight
1390
1390
1390
jeff@lap-jeff:~$ pastebinit /var/log/Xorg.0.log
http://paste.ubuntu.com/6366852/


```

All the best
Jeff

---

### Post by Toz on 2013-11-05
The kernel parameter didn't take. Can you try the following instead (from a terminal window):

1. Open the grub configuration file for editing:
[LIST]
[*]If using Ubuntu:
```
sudo -i gedit /etc/default/grub
```
[*]If using Kubuntu:
```
sudo -i kate /etc/default/grub
```
[*]If using Xubuntu or lubuntu:
```
sudo -i leafpad /etc/default/grub
```
[/LIST]
...and enter your password when prompted.

2. Change the line that reads:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

3. Save the file.

4. Commit the change:
```
sudo update-grub
```

5. Reboot and test. Again, post back the results of the commands if it doesn't work.

---

### Post by jeffhaddow on 2013-11-05
Hello Toz

Many thanks -- that last change has fixed the problem.

All the best 
Jeff

---

