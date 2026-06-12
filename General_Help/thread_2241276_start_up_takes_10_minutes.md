---
title: "start up takes 10 minutes"
date: 2014-08-25
forum: General Help
---

### Post by eddeheer on 2014-08-25
I have gone from ubuntu 12.04 to 14.04 LTS but now it takes 10 minutes before I see the log in screen. When I start my computer I only see a purple rim at the borders of my screen. This lasts for 10 minutes and then the login screen comes up. After loggin in, it works perfect. 

How can this long start up time be solved.

---

### Post by sp40140 on 2014-08-25
what are the specs of your machine?
Did you encounter any issues with upgrade?
You can check the /var/boot.log for any unusual activity during boot process.

---

### Post by eddeheer on 2014-08-25
I have a intel core 2 processor and 4gb RAM. With 12.04 there was no problem. I had no problems with the upgrade

---

### Post by eddeheer on 2014-08-25
/var/boot.log doesnot exist

---

### Post by sotiris2 on 2014-08-25
Its /var/log/boot.log

---

### Post by varunendra on 2014-08-25
Any dedicated graphics card? Nvidia or ATI?

You can generate a full hardware listing with -
```
sudo lshw -sanitize > Desktop/lshw.txt
```
It will create a file named "lshw.txt" on your desktop, containing a list of all your hardware and their relevant specs/configuration details including the drivers in use. Any potentially sensitive info will be automatically filtered out due to the "-sanitize" option in the command above.

You can post this listing at pastebin.ubuntu.com, and post here the link to the pastebin (the pastebin URL that you get after 'pasting' the list there).

Pastebin is a good option to post lengthy logs as well *(you may have to also take a look at 'syslog, Xorg.0.log' etc in the same '/var/log' directory, in case the boot.log couldn't give any significant hints)*. It saves space on forum server. But if posting logs/outputs here, make sure to use **'Code'** tags to preserve their formatting. Please follow the "Use Code Tags" link in my signature to see how.

---

### Post by pqwoerituytrueiwoq on 2014-08-25
[bootchart](apt:bootchart) can also be helpful it will put charts in /var/log/bootchart/

---

### Post by eddeheer on 2014-08-26
I ran bootchart. It takes exactly 900 seconds before the machine starts booting after I pressed the button. On the chart you don't see any activity in this 900 seconds. My graphic card is a Intel® Q33 x86/MMX/SSE2. 



I cannot show the chart here

---

