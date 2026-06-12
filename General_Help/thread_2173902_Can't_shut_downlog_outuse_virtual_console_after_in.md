---
title: "Can't shut down/log out/use virtual console after installing nVidia driver"
date: 2013-09-11
forum: General Help
---

### Post by tehvulpes on 2013-09-11
A while ago I installed some nVidia drivers for my graphics card (GeForce GTX 770), and have been having problems ever since. Whenever I try to log out, shut down, restart the computer, or switch to a virtual terminal with Ctrl+Alt+F_, the display turns off (as if I turned off the computer, it displays a "no information" box) and the computer hangs indefinitely. Everything is still running, and I can still SSH into the computer, do "sudo service lightdm restart", and get sent back to a graphical login screen. After doing that, even after just trying to change to a virtual terminal, the only account logged into the computer is the current graphical session. Once, after trying to switch to a terminal, I typed my name and password  in blindly. After SSHing into the computer and doing "who", I saw that I  was logged in in both the virtual terminal and the graphical session, so it seems the only thing failing is the graphics driver.

[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

When installing the drivers, I used that guide. Because nothing showed up under the "Additional Drivers" tab on the software sources, I had to use the "Method 2: Manual install from repository" he wrote about.
Being able to shutdown and use virtual terminals is more important to me than having the nVidia drivers is, but any help in solving this would be greatly appreciated!

Edit: I forgot, but I should probably mention that I'm using Ubuntu 13.04

---

### Post by Casper Hansen on 2013-10-22
"As usual, NVIDIA should be issuing an updated proprietary Linux graphics driver soon to officially support the GeForce GTX 770. Expect the GTX 770 Linux support to be on-par with the Windows features and performance. The NVIDIA GeForce GTX 770 will likely work with the Nouveau driver soon (if not already), but there for Kepler they don't yet have any re-clocking support and other features yet." 

[http://www.phoronix.com/scan.php?page=news_item&px=MTM4MTc](http://www.phoronix.com/scan.php?page=news_item&px=MTM4MTc)

---

