---
title: "Need Help before Linux installation"
date: 2006-11-09
forum: General Help
---

### Post by Ptah on 2006-11-09
I have been using the Ubuntu 6.10 live cd to test the linux waters. One big concern I have is I can only get a resolution of 1620x1200. How do I get 1920x1200? My system specs are dell 2405 fpw and SLI 7800 GTX.
The only other distros that I have tried are open suse 10.1, Pclinuxos and Mandriva one and they all can run at 1920x1200 without any reconfiguring.

thanks
Ptah

---

### Post by ner0tic on 2006-11-09
upon installation it will auto configure your video settings and need be you can tweak them after.  the live cd has some limitations of functionality due to space constraints and things.

---

### Post by Ptah on 2006-11-09
That is great to hear, is this a common thing with the live cd's?  I am just nervous about installing and it turns out I cant get the resolution to work at startup, it sucks looking at black bars on the sides right now!

---

### Post by ner0tic on 2006-11-09
more or less.. most of the time with most flavors the live cd is used as a gui for installation.. knoppix and some others excluded of course.

---

### Post by ner0tic on 2006-11-09
more or less.. most of the time with most flavors the live cd is used as a gui for installation.. knoppix and some others excluded of course. there are a lot of different video cards so using generic drivers makes for faster bootups for the live discs and such

---

### Post by Ptah on 2006-11-09
Thank you for help!  I have been bouncing from distro to distro looking for the shortest learning curve but this issue has been weighing against Ubuntu.  I now can move it to the top with the others and finally decide.

---

### Post by ner0tic on 2006-11-09
if your on teh fence, it may not hurt to install vmware and install some different flavors using that to get a better feel, but keep in mind it won't be exactly the same as if were on the machine itself you still have a program int eh middle of the os and the hardware. but gives a closer feel than the live cds.

---

### Post by Scheater5 on 2006-11-09
Complete personal opinion, but ubuntu most definitely has an incredibly short learning curve compared to most distros.  Of course, how short the learning curve is will depend on the individual, and your milage may vary.  
Given that, Ubuntu 6.10 has had some problems recognizing monitor size.  There is the possibility that even after a hard disk install it will still not immediately allow you to increase the resolution to it's maximum size.  I would like to emphasize "immediately" - because it's a relatively easy fix (there are a couple of options, and if all else fails you can manually edit a file called X.org to make Ubuntu see your screen as the size you want it to).  But I would also try Ubuntu 6.06, as it seems to have occurrences of this problem less often, and as the LTS (that's "long term support") edition may be more suited to a beginner, depending on your needs.

---

### Post by strabes on 2006-11-10
My monitor wouldn't give me anything above 1024x768 until I installed my video card drivers. (fglrx for ATI) If it doesn't work after you install ubuntu, first thing you should do is install your video card drivers.

---

### Post by Ptah on 2006-11-18
I finally was able to install Ubuntu but I have the same question as above sorry for the repeat. I am using a dell 2405 fpw monitor How do I change my resolution from the the ubuntu max of 1620x1200 to 1900x1200.  Do have to edit the xorg file this sucks for a newbie.  The one thing I do have is my monitor specs infront of me so I hope this will help.  I once again look forward the the forums guidence!

---

### Post by ner0tic on 2006-11-18
what video card do you have?

after that's determined get the newest drivers.

install them, then run dpkg-reconfigure xserver-xorg (or your drvers' config...

(ie: with my radeon i use aticonfig)

---

### Post by Scheater5 on 2006-11-18
ner0tic gives you good advice.  If that doesn't work, try telling Ubuntu you have a "generic" monitor for a monitor of your size or maybe larger (larger is what worked for me).  You can find this under your settings (for KDE this is K menu>System Settings>Monitor and Display>Hardware>[appropriate monitor] - you'll have to ask someone else for the exact method in Gnome).  This is a much simpler solution than editing X.org, however if the problem is something more fundamental than just incorrect hardware recognition it may not solve the problem.  This method also leaves your graphics card driver as it is, in case you already have the newest drivers or have done any more configuring of that sort.

---

### Post by Ptah on 2006-11-18
I have (2) nvidia 7800 gtx cards set to sli. Where do I go to get newest drivers?  If I were using windows I would go straight to Nvidia.  Do I use the same process?

---

### Post by igknighted on 2006-11-18
You can go straight to NVIDIA if you want, but I would recommend adding this repository to your /etc/apt/sources.list file (can be done through synaptic if you prefer):
```
deb http://amaranth.selfip.com edgy lrm
```

After this is added, you can install the nvidia-glx package and get the very latest drivers.

---

### Post by Ptah on 2006-11-19
Ok, as a big time newbie, how do I add the repository?  I know how to get to Synaptic package manager, settings, repositories but from there where?

I was just reading and found this please correct me if I am wrong:

1. Select system, admin, synaptic manager
2. search for nvidia-glx, install package
3. then open terminal Applications, accessories and type sudo nvidia-glx-config enable
4. reboot
5. then to further config the card open up terminal again and type nivida-settings

Also I am using Dapper lts

---

### Post by helliewm on 2006-11-19
You may want to take a look at this sticky I followed and it works.

[http://www.ubuntuforums.org/showthread.php?t=301499](http://www.ubuntuforums.org/showthread.php?t=301499).

Helen

---

### Post by igknighted on 2006-11-19
I believe that what you just typed will install the latest NVIDIA 8xxx series  driver.  The repository I gave will install the latest 9xxx series driver (which is still in beta).  My rationale was that if you are using SLI then the newest driver series may be necessary.  I am not sure how to add repo's through synaptic.  I do all my package management through the terminal, I just think its easier and quicker than waiting for a GUI.  This is how I would do it.  In the terminal type:
```
sudo gedit /etc/apt/sources.list
```
This will open the text file with the list of repositories on it.  Add this line to it:
```
deb http://amaranth.selfip.com dapper lrm
```
The run these commands, one line at a time:
```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-glx config enable
```
Then do a system restart and you should be set

---

### Post by Ptah on 2006-11-19
When I get to the terminal and type the first command it asks for the password.  I try to type it but the blinking cursor does not move to indicated I have typed.

---

### Post by Irony on 2006-11-19
The cursor won't show anything just type your password and hit enter.

Note that when you open a graphical program such as gedit you should use;

[PHP]gksudo gedit[/PHP]

Whilst as it happens it makes no difference with gedit you may find  that you lock yourself out of the system with say using;

[PHP]sudo nautilus[/PHP]

When you should use;

[PHP]gksudo nautilus[/PHP]

---

### Post by Ptah on 2006-11-19
I did type the password but it says sorry, try again.  I know my password its correct because when I got to synaptic I must type in.  Ok I tried gksudo gedit and an unsaved doc 1 -gedit opens up.  From there do just type in what igknighted sayed?

For some reason no it works I am the source.list, do add deb [http://amaranth.selfip.com](http://amaranth.selfip.com) dapper lrm at the beginning?

---

### Post by Irony on 2006-11-19
Note if you do an nvidia search in synaptic you may already find compatible drivers in the repositories - as a newbie this would be the easiest way to start.

You may also want to look at the wiki regarding nvidia;

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=nvidia&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=nvidia&titlesearch=Titles)

---

### Post by Ptah on 2006-11-19
I ran the the aramath list but It said:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) dapper Release.gpg
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://amaranth.selfip.com](http://amaranth.selfip.com) dapper/lrm Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Err [http://amaranth.selfip.com](http://amaranth.selfip.com) dapper/lrm Packages
  404 Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Fetched 3B in 0s (4B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
E: Couldn't rebuild package cache

---

### Post by Ptah on 2006-11-19
I deleted aramath and went to the synapitc install nvidia-glx which installs the 87 drivers and it turns out that 1600x1200 looks alot better than before.   Text is alot crisper and not stretched out, although I still can not get 1900x1200 res it will due until I learn how to edit the xorg file to add addition resolutions.  Thanks for everyone's help!

---

### Post by Irony on 2006-11-19
To edit xorg file first make a backup of the file;

[PHP]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup[/PHP]

Then open up the file;

[PHP]gksudo gedit /etc/X11/xorg.conf[/PHP]

Go to the sections that say something like;

[PHP]"1280x1024" "1600x1200" "800x600" "640x480"[/PHP]

And add to them;

[PHP]"1900x1200" "1600x1200" "1024x768" "800x600" "640x480"[/PHP]

With a bit of luck this option will pop up in;

*System > Preferences > Screen Resolution*

Note though that it may simply go to a blank screen in which case you'll have to reinstate the back_up copy.

---

