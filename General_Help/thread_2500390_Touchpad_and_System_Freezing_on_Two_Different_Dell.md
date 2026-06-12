---
title: "Touchpad and System Freezing on Two Different Dell Latitude 7410 Devices After Ubuntu"
date: 2024-08-31
forum: General Help
---

### Post by rowayda on 2024-08-31
**Issue with Touchpad and System Freezing on Two Dell Latitude 7410 Devices After Installing Ubuntu 24 Alongside Windows**

I recently purchased two used Dell Latitude 7410 laptops (i5-10310U, 16GB RAM, 256GB SSD, FHD Touchscreen 360-degree) and installed Ubuntu 24 alongside Windows on both.
**Here's what happened:**

[LIST]
[*]**First Device:**
[LIST]
[*]After installing LAMP and some work apps, everything seemed fine&#8212;until I opened SoundCloud in Google Chrome. The touchpad started freezing repeatedly.
[*]I also noticed the touchpad hung for a brief moment during the Ubuntu installation process itself.
[/LIST]

[*]**Second Device:**
[LIST]
[*]I exchanged the first laptop for another with the same specs. This time, after a similar installation and partition setup (30GB for Windows, 50GB ext4 for root, 16GB swap, and the rest for /home), the touchpad and the entire system started freezing again, but only after playing a YouTube video.
[/LIST]
[/LIST]
**Additional Observations:**

[LIST]
[*]The freezing issues aren't limited to Ubuntu&#8212;it's also happening in the BIOS. The touchpad hangs, though the touchscreen still works.
[*]When I restart the laptop, it goes directly to Ubuntu, even though "Windows Boot Manager" is listed in the BIOS boot sequence. Windows isn&#8217;t shown as an option.
[/LIST]
The store confirmed that Windows alone doesn&#8217;t have any problems, which leaves me stumped.

**Has anyone else experienced similar issues with this model? Any ideas or potential solutions?**

Your insights would be greatly appreciated!

---

### Post by amrali on 2024-09-01
Have you run [HTML]sudo apt update -y && sudo apt full-upgrade -y && sudo apt dist-upgrade -y[/HTML] after installation ubuntu
Have you checked if you have any broken packages 
What is happen when you use USB mouse , Is the hanging issue still exist ?????? 
Have this issue appeared when you perform the installation of ubuntu ???????

Try to make some changes to the sources.list with taking a backup from the original sources.list file and see if the problem still exists 

Hope it helps

---

