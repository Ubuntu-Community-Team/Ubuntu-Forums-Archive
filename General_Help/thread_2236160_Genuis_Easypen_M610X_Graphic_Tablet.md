---
title: "Genuis Easypen M610X Graphic Tablet"
date: 2014-07-24
forum: General Help
---

### Post by SMiller FTP on 2014-07-24
Greetings everyone. 

I have a Genuis Easypen M610X Tablet connected to my Kunbutu  desktop computer. It can respond and move  the curser and click as well.  But when I used it for Krita or Gimp it won't draw anything. I found that Kunbutu alone has yet to make it compatible yet for my version of the  tablet. I've installed wizardpen from the terminal to my computer, but my tablet   still won't work nor will it show up on the Graphic Tablet tab from  the Input Devices, in the System Setup. I also came upon some patches called DIGI*mend *that said it will fix and get it to working. Here's the link [http://sourceforge.net/projects/digi...rnel-packages/]("http://sourceforge.net/projects/digimend/files/kernel-packages/").
 But this is where I'm having the problem. I can't seem to figure out  how to put the patch on to my kernal and the offical site for doesn't say much on how to do that. And I'm affraid to mess things up  as I've managed to get it to working smoothly now. 

Here is more software info about my device for use based from the commands "lsusb" and "xinput list"
          
&#8627; Genius EasyPen M610X                      id=11   [slave  pointer  (2)]
Bus 006 Device 002: ID 0458:5013 KYE Systems Corp. (Mouse Systems) 


Also here is my OS info: 
Version 14.04 64-bits
KDE     Platform Version 4.13.2
GRUB Version: 0.97-29ubuntu66
Kernal 3.13.0-32-generic
;this is the main operating system for my computer.
It's not a dual boot, there are no other OS installed.

I didn't see  any similiar posts like this here on this forum so far, for my  situation. 
Any advice or help on how to install this or have another way to get the tablet to work, it would be very appreciated.
If more info is needed then what's provided, I will provide it as best I can.
Also, if there are any websites, books or other sources that I can look  into to give me more info on what I'm doing to help me out would be  greatly as well.

Thanks to all that help.

---

### Post by dave131 on 2014-07-24
See if this link helps:  [https://help.ubuntu.com/community/TabletSetup](https://help.ubuntu.com/community/TabletSetup)

---

### Post by SMiller FTP on 2014-07-25
It seem to not help much. 
Though, I've been to that site before and tried to do the methods it instructed on this page: [URL="https://help.ubuntu.com/community/TabletSetupWizardpen"]Link
[/URL]I  followed the methods again as instructed, but still getting some errors  and roadblocks on some step including error message, unable to find  file or locate package, on methods 1 & 2, [SIZE=2]setting up X[/SIZE] and other that are on there. I don't know if I'm doing it wrong, or that it is just not avaliable.
Sorry for not stating that at the beginning.

Though glad you offer your assistance.

---

### Post by dave131 on 2014-07-28
I can't guarantee I can help you, but perhaps we should try going one step at a time.  Post exactly each step - the exact text you are typing, etc. - and when you get to the first error, stop and report that error.  Perhaps we can work through things easier that way.  For anyone to help, we'd need to know the exact steps you are taking, where it fails, the exact error messages, etc.  Screen shots attached to the post a great way for us to see what is happening.  I'm currently running lubuntu, so I don't know if the name is the same in regular ubuntu, but in lubuntu the application is called screenshot.  I find it best to set it for current window with a delay of about 2 or 3 seconds.

---

### Post by SMiller FTP on 2014-07-31
Okay, first I went here; [Link]("http://help.ubuntu.com/community/TabletSetup"). I started by Identifying my touch screen vendor method. I put in the "cat /sys/bus/usb/devices/*/product" command and got these results. 

```

User@User-GA-78LMT-S2P:~$ cat /sys/bus/usb/devices/*/product
802.11 n WLAN
Optical USB Mouse
Comfort Curve Keyboard 2000
EasyPen M610X
C-Media USB Audio Device   
EHCI Host Controller
EHCI Host Controller
OHCI PCI host controller
OHCI PCI host controller
OHCI PCI host controller
OHCI PCI host controller
OHCI PCI host controller

```

My device "Easypen M610x" is listed. So, I went to the Wizardpen driver section and click the link below; [TabletSetupWizardpen]("http://help.ubuntu.com/community/TabletSetupWizardpen").

Next, I started from method 1 and did the repository and got that put in the Moun Discover. 
After that I did an update in the konsole. Once finished I did the installion of xserver-xorg-input-wizardpen program and got this message that states "The following packages were automatically installed and are no longer required:" and these were the two thing that showed underneith, "linux-headers-3.13.0-30 linux-headers-3.13.0-30-generic" "linux-image-3.13.0-30-generic linux-image-extra-3.13.0-30-generic".

After which I went to do the calibration method skipping the configuration one for it stated underneath "For Jaunty (9.04) release:". So, first thing I did was the "cd calibrate" command and got "bash: cd: calibrate: No such file or directory". So afterwhich I dicided to skip that step as well and went to the Setting up X method. I start by typing in "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup" and got "cp: cannot stat ‘/etc/X11/xorg.conf’: No such file or directory". After that, I decided something must be wrong and went to the X11 directory and saw no xorg.conf file. 

Hope this is what you meant? If not I will go back and do another over again with more detail if I can.

Here are the screeenshots and text from the konsole/terminal of the commands and responses I got.

```

User@User-GA-78LMT-S2P:~$ sudo apt-get update
[sudo] password for User: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
User@User-GA-78LMT-S2P:~$ sudo apt-get update
Hit http://repo.steampowered.com precise InRelease
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security Release                         
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://repo.steampowered.com precise/steam amd64 Packages                                                                                             
Hit http://us.archive.ubuntu.com trusty Release                                                                                                           
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty-updates Release                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Ign http://archive.canonical.com trusty/partner Translation-en                 
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://us.archive.ubuntu.com trusty-updates/main Sources         
Hit http://ppa.launchpad.net trusty Release.gpg                      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources   
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources     
Hit http://ppa.launchpad.net trusty Release.gpg                      
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Hit http://ppa.launchpad.net trusty Release.gpg                      
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources   
Ign http://ppa.launchpad.net trusty Release.gpg                      
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages  
Ign http://repo.steampowered.com precise/steam Translation-en_US     
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Ign http://repo.steampowered.com precise/steam Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://ppa.launchpad.net trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://ppa.launchpad.net trusty Release
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Ign http://ppa.launchpad.net trusty Release    
Ign http://ppa.launchpad.net trusty Release    
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://ppa.launchpad.net trusty Release
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://ppa.launchpad.net trusty Release    
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://ppa.launchpad.net trusty Release    
Hit http://us.archive.ubuntu.com trusty-backports/main Sources        
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://ppa.launchpad.net trusty Release
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources    
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Ign http://ppa.launchpad.net trusty Release
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://ppa.launchpad.net trusty Release
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://ppa.launchpad.net trusty/main Sources
  404  Not Found
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/trusty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/vokoscreen-dev/vokoscreen/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/vokoscreen-dev/vokoscreen/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
User@User-GA-78LMT-S2P:~$ sudo apt-get install xserver-xorg-input-wizardpen
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-input-wizardpen is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-30 linux-headers-3.13.0-30-generic
  linux-image-3.13.0-30-generic linux-image-extra-3.13.0-30-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
User@User-GA-78LMT-S2P:~$ cd calibrate
bash: cd: calibrate: No such file or directory
User@User-GA-78LMT-S2P:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
cp: cannot stat ‘/etc/X11/xorg.conf’: No such file or directory

```

---

### Post by dave131 on 2014-07-31
The first thing that comes to my mind is that there is no /etc/X11/xorg.conf by default now.  You can generate a skeleton, just create your own with only those parts you need.

---

