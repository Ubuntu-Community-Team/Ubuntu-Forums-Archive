---
title: "Samsung Laptop brightness issues"
date: 2015-03-28
forum: General Help
---

### Post by Gian_Lorenzo_Spiss on 2015-03-28
I recently installed Ubuntu 14.04 on my Samsung Ativ Book 6 (NP680Z5E-X01US).


Since then I am completely unable to modify my brightness settings. The Fn buttons work fine, if I press Fn+F2/F3 I can see the brightness slider, but no change happens until I push it down to where it deactivates the screen. Also, there is no response from the keyboard backlight. Other work fine (audio, wifi, mousepad-lock)


I have tried several options and I am essentialy in the same spot of the user here:


[http://askubuntu.com/questions/70552/cant-adjust-brightness-on-my-msi-vr420-laptop?rq=1](http://askubuntu.com/questions/70552/cant-adjust-brightness-on-my-msi-vr420-laptop?rq=1)


What I tried:


 - Edit /etc/default/grub &#8614; GRUB_CMDLINE_LINUX_DEFAULT: acpi_osi=Linux,
   acpi_backlight=vendor (as well as several different combinations of
   these settings being on or off)
   
 - Edit /etc/X11/xorg.conf (file doesn't exist on my system)
   
 - sudo setpci -s 00:02.0 F4.B=XX (does nothing)
   
 -  xbacklight -set XX (does nothing)
   
 - install indicator-brightness (changing its value does nothing)


Checking the folder


    ```
ls /sys/class/backlight/intel_backlight/
```


shows that


    ```
max_brightness = 4882
```


while

```

    actual_brightness
    brightness

```

change as I move the slider in step of 244, but no corresponding change in brightness happens.


My graphic card is


    ```
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)       

```

I also have a Radeon 


    ```
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] (rev ff)
```

Can anybody offer any piece of advice? I am very novice and don't know how to proceed.

---

### Post by Gian_Lorenzo_Spiss on 2015-03-29
Bump for edit listing all things tried sofar. Anybody has any advice?

---

### Post by Gian_Lorenzo_Spiss on 2015-04-02
Help plz

---

### Post by Toz on 2015-04-02
Looks like it might be [this bug]("https://bugzilla.kernel.org/show_bug.cgi?id=84561") that has been fixed in kernel 3.19.

[Here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1380824") is associated launchpad bug with information on how to try the 3.19 kernel.

---

