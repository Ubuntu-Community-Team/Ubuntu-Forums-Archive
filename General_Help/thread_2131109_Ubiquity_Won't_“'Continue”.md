---
title: "Ubiquity Won't “'Continue”"
date: 2013-03-31
forum: General Help
---

### Post by Mike Green9 on 2013-03-31
March.30.2013
Ubuntu 12.10          gnome 3.6.0
ubiquity                   2.12.16
ubiquity-casper         1.328                                                        
 ubiquity-frontend-debconf   2.12.16      (required by remastersys)                                                
 ubiquity-slideshow-ubuntu     65                                                           
 ubiquity-ubuntu-artwork          2.12.16                                                      
 remastersys                        3.0.4-2
 
 Hi.
 
 I have been using remastersys to build ISO files successfully up until Feb.3.2013. On Mar.27, I built a fresh remastersys 3.8gb ISO, and burned it to a DVD. I swapped out my live hard drive for a backup drive.  

 The backup drive is partitioned with Windows 7, 2 data partitions, a Linux swap partition, and an ext4 25gb empty partition (formatted by GParted).
 
 The purpose of the exercise is to xfer my live desktop onto the 25gb empty partition on the backup drive.
 
 I boot the freshly burned DVD, my desktop comes up, and I click on the 'install' icon. This kicks ubiquity into gear: ubiquity --desktop %k gtk_ui
 
 Ubiquity asks for 'Language', and then goes into the 'Preparing To Install' screen where it displays available Space, internet connection, & 3rd party software.
 
 I click 'continue' and Ubiquity asks for 'Installation Type' . I enter 'something else' and fill in applicable information (destination & boot partitions). I click 'Install Now'.

 Ubiquity asks 'Where Are You?'. I enter my location  & click on 'continue'.
 
 Ubiquity asks for 'keyboard' info. I click on 'English US' and 'continue'.
 
Now is where the problem starts. Ubiquity should ask 'Who Are You?', but it misses this screen and goes into an unfamiliar screen asking me to
'Choose A Picture'  or  'Select An Existing One'. (This was never asked on on the Feb.3 DVD.) Note that part of the previous 'keyboard info' screen is erroneously displayed.

 I select an 'Existing' icon, but the  'Continue' box remains 'greyed', leaving me no way to continue &#8211; only go 'back'.
 
In the mean time, files are being copied from the DVD to the hard disk. When the copying is done, Ubiquity waits indefinitely for my useless attempt to click on the 'greyed' out 'contuinue' box.
 
 I retried my Feb.3 DVD, and it works fine. I tried buidling new DVDs (via remastersys) on Mar.28, & Mar.29. All fail in the same way.

 I've managed to work my way around several Ubiquity quirks in the past, but I'm stuck at this point. The only changes to my system since Feb.3 are the regualr system updates.
 
 I tried re-installing all the applicable Ubiquity packages (above) via Synaptic Package Manager to no avail.

I realize I could use GParted to copy the partition. However, I like remastersys, and intend to use it to update my laptop. With Ubiquity malfunctioning, remasterys is useless. 
 
 Any thoughts would be greatly appreciated.
 

 M....

---

### Post by reia on 2013-06-07
I had the same problem on linux mint 14 mate edition (based on ubuntu 12.10).
This is a possible solution (it worked in my case).
1)install ubiquity-frontend-kde (since gtk does not work...)
2)sudo ubiquity
after a while the frontend installer starts. Anyway, you cannot
set up the user during the installation process.

---

