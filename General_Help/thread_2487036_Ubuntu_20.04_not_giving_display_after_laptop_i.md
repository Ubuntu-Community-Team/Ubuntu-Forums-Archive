---
title: "Ubuntu 20.04 not giving display after laptop i"
date: 2023-05-21
forum: General Help
---

### Post by ahmex03 on 2023-05-21
I have Ubuntu 20.04 installed on my HP Pavilion G series laptop. I have a problem that whenever I close lid of my laptop or laptop goes to sleep, there is no display after lid is reopened or keys are pressed to wake up the laptop.

-----

I tried reinstalling the OS but the problem is still there as it is.

-------

i also tried following steps from this guide [https://askubuntu.com/questions/1032633/18-04-screen-remains-blank-after-wake-up-from-suspend](https://askubuntu.com/questions/1032633/18-04-screen-remains-blank-after-wake-up-from-suspend) . It didnt worked too

$ sudo gedit /etc/default/grub

Then adding **nouveau.modeset=0**  to the line that says **GRUB_CMDLINE_LINUX**.[B]

GRUB_CMDLINE_LINUX="nouveau.modeset=0"[/B]**$ sudo update-grub**[B]

 [/B]reboot

-----

When I execute **systemctl suspend** the LED goes to sleep but no display appears when I press any key.

-----

$  lspci | grep VGA 
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]

-----

can anyone help ???

---

### Post by MAFoElffen on 2023-05-22
??? Wrong boot option for your hardware...

Please backup and post the output of these, posted within CODE Tags:
```

sudo  lshw -c video | grep -e 'product' -e 'driver'
sudo dmesg | grep -i 'amdgpu\|radeon\|i915'
sudo lsmod | grep -i 'amd\|radeon\|i915'
echo $XDG_SESSION_TYPE
grep . /sys/module/*_idle/parameters/max_cstate 2> /dev/null
ls /sys/module/*_idle/parameters/max_cstate

```

---

