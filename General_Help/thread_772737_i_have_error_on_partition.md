---
title: "i have error on partition"
date: 2008-04-28
forum: General Help
---

### Post by jehad4t on 2008-04-28
Hi ....
i`m a new user in linux Ubuntu 7.04

i have error on partition  :confused:

step 1  :  starting the Computer 

[IMG]http://up4.m5zn.com/photos/00037/MDQ7GLZATCRA.jpg[/IMG]

Faild to read splash image ((hd0,2)/boot/grub/splashimages/debian-morebule-swirl.xpm.gz)
Press any key to cantinue ....

i pressd Enter 

step 2 : boot secreen 
[IMG]http://up4.m5zn.com/photos/00037/GN4NP6QEG1WJ.jpg[/IMG]

linux ubuntu
windows xp
------------------------------------
linux ubuntu recovery mode
linux ubuntu momory test
chaniload into grub 2 

i pressd - linux ubuntu 

step 3 : 
[IMG]http://up4.m5zn.com/photos/00037/MDQ7GLZATCRA.jpg[/IMG]

Error 17 connot mount selected partition
Press any key to cantinue ....

i pressd Enter   

when i press enter in step 3 it gets back to secreen step 2



-----------------------

---

### Post by krelverehan on 2008-04-28
One thing... You don't need to have your screen shots so big. It is hard on us with low bandwidth :) 

A few extra questions which might help us solve your problems:

1. Can you start in recovery mode?
2. Can you load windows properly?
3. When you installed ubuntu did it install without errors?

It might be more relevant if you were using the new flavour of ubuntu - 8.04 rather than 7.x. You might just want to try to reinstall ubuntu if it is a fresh install, since you'll have no data to lose.

If you choose to reinstall ubuntu and you are using the live CD, type [FONT="Courier New"][COLOR="RoyalBlue"]sudo gparted[/COLOR][/FONT] into a terminal and try checking the partitions for errors. **note: be careful with gparted, it is a dangerous program if misused.

---

