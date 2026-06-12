---
title: "i cant make brightness down"
date: 2012-12-08
forum: General Help
---

### Post by raultry on 2012-12-08
Hi, i want to fix my rbrightness of my computer, i have a hp pavilon dv7

i have downloaded the brightnessup.sh and the brightnesdown.sh, and when i run it, the scripts says that: 
[HTML]./video_brightnessdown.sh: line 33: /proc/acpi/video/VGA/LCD/brightness: No such file or directory
[/HTML]
so i wanted to create this file, that the content is this:

[HTML]levels: 70 40 0 10 20 30 40 50 60 70
current: 30
[/HTML]
and i want to create directory of the file brightness, but, when i try this me says that

[HTML]mkdir: cannot create directory `video': No such file or directory
[/HTML]

i have linux mint 14

i dont know how to fix the brighness, is the only one that i dont have for the funcionality of my computer

someone can help me?

---

### Post by pqwoerituytrueiwoq on 2012-12-08
try using [xbacklight](apt:xbacklight)

---

### Post by raultry on 2012-12-08
> **pqwoerituytrueiwoq said:**
> try using [xbacklight](apt:xbacklight)

thanks for your reply, but results that i tried with xbacklight and nothing :(

i want to create this structure of directories becaouse i have the sense thar i have to have the file brightness in the directory named before

---

### Post by raultry on 2012-12-08
> **raultry said:**
> thanks for your reply, but results that i tried with xbacklight and nothing :(

i want to create this structure of directories becaouse i have the sense thar i have to have the file brightness in the directory named before

Noting to say? :(, i need help

---

### Post by steeldriver on 2012-12-08
I think the /proc/acpi/video kernel interface is deprecated 

You won't just be able to make your script work by creating that directory tree - /proc is a system directory that gets populated at boot time based on your detected hardware

Have a look in /sys/class/backlight and see if there's an entry like

```
/sys/class/backlight/acpi_video0/brightness
```If so it should be possible to change the brightness by doing either

```
$ echo *n* | sudo tee /sys/class/backlight/acpi_video0/brightness
``` or

```
$ sudo sh -c "echo *n* > /sys/class/backlight/acpi_video0/brightness"
```where *n* is the desired brightness value - you should probably look at the max_brightness to decide what value to use

```
$ cat /sys/class/backlight/acpi_video0/max_brightness
```[https://wiki.ubuntu.com/Kernel/Debugging/Backlight#Checking_the_kernel_interfaces](https://wiki.ubuntu.com/Kernel/Debugging/Backlight#Checking_the_kernel_interfaces)

---

### Post by raultry on 2012-12-09
> **steeldriver said:**
> I think the /proc/acpi/video kernel interface is deprecated 

You won't just be able to make your script work by creating that directory tree - /proc is a system directory that gets populated at boot time based on your detected hardware

Have a look in /sys/class/backlight and see if there's an entry like

```
/sys/class/backlight/acpi_video0/brightness
```If so it should be possible to change the brightness by doing either

```
$ echo *n* | sudo tee /sys/class/backlight/acpi_video0/brightness
``` or

```
$ sudo sh -c "echo *n* > /sys/class/backlight/acpi_video0/brightness"
```where *n* is the desired brightness value - you should probably look at the max_brightness to decide what value to use

```
$ cat /sys/class/backlight/acpi_video0/max_brightness
```[https://wiki.ubuntu.com/Kernel/Debugging/Backlight#Checking_the_kernel_interfaces](https://wiki.ubuntu.com/Kernel/Debugging/Backlight#Checking_the_kernel_interfaces)

i try this but nothing

---

