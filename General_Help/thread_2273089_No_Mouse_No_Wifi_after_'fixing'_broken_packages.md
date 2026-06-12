---
title: "No Mouse No Wifi after 'fixing' broken packages"
date: 2015-04-10
forum: General Help
---

### Post by ross4 on 2015-04-10
I'm using xubuntu 14.04.02 LTS.  
 

 This is what I THINK transpired, though I'm pretty sure I've left out some steps I took. I got a notice to update but the update failed and left broken packages. There was a red warning icon. Based on what I read and a previous warning, I thought that I might be out of space. So, using the package manager, I completely removed “Celestia”, a program that I had installed quite a while back but seldom used. After that, the warning icon was gone and I re-booted and did sudo apt-get update and a clean. Things  seemed to work fine except that my mouse failed. I thought it was the batteries and changed them. Still didn't work. Double checked the mouse and receiver on a different computer (also using xubuntu) and it worked fine. Used lsusb and found Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver  so I know that the machine knows the mouse receiver is there. Thought I would search for help here and found that my WiFi connection suddenly wasn't working. Now I've got the cable attached so I can connect and ask “Now what do I do!”   
 Any help toward diagnosing the problem is welcome.
Regards,
Ross

---

### Post by ross4 on 2015-04-11
Hmmm, no responses so far. Well, here is an update that might trigger  some ideas. I used a Linux Mint DVD and an Ubuntu thumb drive to test  the machine with the live option and found that I could get everything  working (mouse, Wifi) so I guess my previous futzing around must have  deleted/corrupted some software or settings files. I'm thinking of re-installing xubuntu  (or maybe installing ubuntu because I have that already handy) but I was  wondering if there is a simpler way of getting things back to the way  they were. I've already backed up all my personal data.

Can anyone suggest a method of re-establishing a working installation without a complete re-install?

For what it is worth, my system is dual boot and the hard-drive is formatted as follows:
/dev/sda1 ,  ntfs ,   , 63 GiB
/dev/sda2 ,  extended ,   , 48.79 GiB
/dev/sda5 ,  ext4 , /boot  , 857.00 MiB
/dev/sda6 ,  ext4 , /  , 9.54 GiB
/dev/sda7 ,  ext4 , /home  , 36.32 GiB
/dev/sda8 ,  linux-swap ,   , 2.09 GiB

---

### Post by coffeecat on 2015-04-11
Well - several seemingly unrelated issues, but you've established that your hardware is working by testing with running live sessions of Ubuntu and Mint. And you've already backed up your personal data. You may be lucky and find that your old installation is easy to fix, or you may spend many frustrating hours tracking down problems. If I was in your situation I would simply go for the fresh re-install.

---

### Post by Keith_Helms on 2015-04-11
Without doing a fresh install of Xubuntu, you could try and find what packages got removed that you didn't intend to.  Take a look in /var/log/dpkg.log and /var/log/apt/history.log and see if anything got removed along with Celestia.  If so, try adding those packages back.

---

