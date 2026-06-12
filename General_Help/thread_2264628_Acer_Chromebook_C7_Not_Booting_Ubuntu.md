---
title: "Acer Chromebook C7 Not Booting Ubuntu"
date: 2015-02-08
forum: General Help
---

### Post by ovingiv on 2015-02-08
Good evening from Plymouth.

I had installed Ubuntu 13.10 LTS on the Acer C7 Chromebook. The UI was still lagging and I could not take it. So I re-installed Chrome OS and went though the steps to install 12.04 LTS and I got it to work but I forgot to change it to have Ubuntu be the default boot. When I go into the terminal (by CTRL+ALT+F2) and type the commands "sudo cgpt add -i 6 -P 5 -S 1 /dev/sda" it gives me no errors and then I restart the device. Once its rebooted it goes to Chrome OS. Is there something I'm doing wrong?

---

### Post by TheFu on 2015-02-09
13.10 support ended. [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) explains.

Please installed a supported OS - probably 14.04 LTS is what you want, unless you can commit to reinstalling the latest release every 6 months.

Also, it would be extremely helpful to know EXACTLY which model of chrombook you have.

---

### Post by oldrocker99 on 2015-02-09
The Acer C7, the original one, with Chrubuntu installed, uses/used the ChromeOS kernel, which if I recall is 3.4 or thereabouts. When Chrubuntu is installed, it does not use the kernel that 12.04 uses. I tried, on a Chrubuntu-loaded Acer C7 (the one with a 350GB hard drive), to use 12.10, and come programs would not work at all, requiring at least the 3.6 kernel. If one stays with 12.04, it'll be supported for another three years.

I rather doubt that 14.04 would work with the Chrubuntu script. I could easily be mistaken, but I could also be right.

---

### Post by TheFu on 2015-02-09
Hopefully the OP will reply ... but that is doubtful.

I've been running stock 14.04 on my C720 for ... 9-ish months. ChromeOS was wiped 5 minutes after it booted the first time. Still have to rebuild the kernel drivers for the touchpad with every new kernel (long ago scripted), but everything besides that works. Fixed the resume-audio issue that has been a slight bother recently.  14.10 has support for the touchpad built-in, but I only run LTS releases for many, many, many reasons. I look forward to 16.04 to end my manual driver compiles.

---

### Post by ovingiv on 2015-02-10
I have the Acer Chromebook C710. But I have an HDMI and 3 usbs. 

Thank you for all the replies. But my issue has since been fixed. The reason why I'm using 12.04 LTS is because I get the best UI experience. Even in 12.10 I had UI lag. When playing videos the video and audio wasn't synced. I couldn't find a fix for it ether. But below is what I did to fix it.

When your on the Chrome OS terminal by CTRL + ALT + F2
Login chronos
Type ```
sudo cgpt add -i 6 -P 0 -S 1 /dev/sda
```
Then type ```
sudo cgpt add -i 6 -P 5 -S 1 /dev/sda
```
Reboot and you should be loading Ubuntu.

---

