---
title: "[SOLVED] brightness issues with inspiron 1501"
date: 2008-01-19
forum: General Help
---

### Post by charlescarroll1 on 2008-01-19
I am having trouble with my brightness controls (FN+Up/FN+Down) on my dell inspiron 1501, they don't work at all unless I'm in Windows or at the grub menu (the brightness applet does not work either).

I've looked at other threads and read that if I update my bios it will solve this problem, but I just updated my bios with still no luck.  

I read in one thread that blacklisting video fixes this problem with the Inspiron 6400, but didn't want to try this with my 1501 unless I know what I'm doing.

So, like I said, the only way I can adjust the brightness is when I'm in Windows or at the grub menu, which can be a real hassle restarting just to adjust the brightness.

Any suggestions?

---

### Post by charlescarroll1 on 2008-02-10
I found some information saying that if I upgrade my BIOS, then I will be able to use the FN+Up and FN+Down keys to adjust the brightness on my laptop.  Unfortunately I haven't had any luck, I updated my BIOS and am still having the same problem.

On the other hand, I did find a way to adjust the brightness inside Ubuntu.  You can run this command.

sudo -s
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness
exit

You can replace the 50 with:
37 12 25 37 50 62 75 87 100

100 is full brightness 50 is half brightness ect.

This is still annoying, but it is a lot easier than restarting and adjusting the brightness at the grub menu :)

---

### Post by fragos on 2008-02-11
I found an additional layer VGA has VID, VID1 and VID2.  Each of these directories has an LCD folder with a brightnes file except the VID2.

---

### Post by OMRebel on 2008-04-30
Actually, there is an easy solution for the brightness controls that I found on another site that works perfect:

sudo gedit /etc/acpi/video_brightnessup.sh

replace everything in the file with

#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/VGA/LCD/brightness |awk '{print $2}')


case "$CURRENT" in

100)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness;
;;
87)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness;
;;
75)
echo -n 87 > /proc/acpi/video/VGA/LCD/brightness;
;;
62)
echo -n 75 > /proc/acpi/video/VGA/LCD/brightness;
;;
50)
echo -n 62 > /proc/acpi/video/VGA/LCD/brightness;
;;
37)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness;
;;
25)
echo -n 37 > /proc/acpi/video/VGA/LCD/brightness;
;;
12)
echo -n 25 > /proc/acpi/video/VGA/LCD/brightness;
;;
*)
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness ;
;;
esac



sudo gedit /etc/acpi/video_brightnessdown.sh

replace everything in the file with


#!/bin/bash

CURRENT=$(grep "current:" /proc/acpi/video/VGA/LCD/brightness |awk '{print $2}')


case "$CURRENT" in

12)
echo -n 12 > /proc/acpi/video/VGA/LCD/brightness;
;;
25)
echo -n 12 > /proc/acpi/video/VGA/LCD/brightness;
;;
37)
echo -n 25 > /proc/acpi/video/VGA/LCD/brightness;
;;
50)
echo -n 37 > /proc/acpi/video/VGA/LCD/brightness;
;;
62)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness;
;;
75)
echo -n 62 > /proc/acpi/video/VGA/LCD/brightness;
;;
87)
echo -n 75 > /proc/acpi/video/VGA/LCD/brightness;
;;
100)
echo -n 87 > /proc/acpi/video/VGA/LCD/brightness;
;;
*)
echo -n 50 > /proc/acpi/video/VGA/LCD/brightness ;
;;
esac

---

### Post by charlescarroll1 on 2008-07-09
Thanks OMRebel!!!

Finally this problem that has plagued me for almost a year has been solved!!!

---

