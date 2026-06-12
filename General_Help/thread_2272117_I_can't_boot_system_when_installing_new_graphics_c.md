---
title: "I can't boot system when installing new graphics card"
date: 2015-04-04
forum: General Help
---

### Post by fkervin on 2015-04-04
Hi all,

I have a Xubuntu system with an intel processor and I was using its integrated graphics card.

Now I've add a new card, an nVidia, and system refuses to boot. I've run Boot Repair Disk but it can't fit it. When I book I get the cursor in a blank screen, but nothing else.

What do I have to do to upgrade the new VGA in way system boots?

Many thanks in advance

---

### Post by ajgreeny on 2015-04-04
Try Ctrl+Alt+F1 to get to a command prompt, and from there run command ```
sudo apt-get install nvidia-current
```
If that is not successful you should be able to boot to a command prompt from the grub menu by:-


[LIST=1]
[*]with the menu item you want to boot highlighted hit "E" for edit.
[*]navigate to the line that ends with **quiet splash** and replace just those two words with **text**.
[*]Control+X to boot with those boot-options for just this one time.
[*]Run command as above to install nvidia-current.
[/LIST]

---

### Post by fkervin on 2015-04-05
Many thanks ajgreeny,

With some work I've reach to the command line, then the problem is I can't install nvidia drivers, when I try "sudo apt-get install nvidia-current" I have this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 nvidia-current : Depends: nvidia-304 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I've try sudo apt-get update and upgrade, sudo apt-get autoremove and some other supposed solutions I've found over the internet, but I can't install nvidia drivers :(

Of couse, I've try to install nvidia-304 but it also shoot the same error with other dependendies, and the packages it shown returns the same error.

Any idea to fix the system in way I can install nvidia drivers?

Regards

---

### Post by oldos2er on 2015-04-05
Try ```
sudo apt-get install -f
``` to fix broken packages.

---

### Post by ubunt72 on 2015-04-05
That's strange that nvidia-current would be 304?   That is the last driver that supports legacy cards.   Shouldn't 'nvidia-current' install 340 at least?   The very latest driver is 346.   Just asking.   Not sure if I'm helping at all. :)

EDIT:   Just looked it up.  

[http://packages.ubuntu.com/search?suite=vivid&keywords=nvidia-current](http://packages.ubuntu.com/search?suite=vivid&keywords=nvidia-current)

Wow, it's using an older driver.   I wouldn't even bother with that package.   Just look up the steps to install 340 or 346?   

Also, the black screen could be a result of it trying to use the open source nouveau driver?    I think there is a way to blacklist or disable nouveau.   Then, it should allow the computer to boot and to install the nvidia driver in the DE?   Using 'Additional Drivers' - as I tried this with the live edition of 15.04 -beta2 and it showed the options including 340 and 346 with my GTX 750.   

I used Ubuntu 15.04-beta2 w/ MATE.

I would try blacklisting nouveau and then try to boot up.   If you can, then install from the repo - using 'Additional Drivers' - if it will work.   

This page has the steps:
[http://ubuntuhandbook.org/index.php/2015/01/install-nvidia-346-35-ubuntu-1404/](http://ubuntuhandbook.org/index.php/2015/01/install-nvidia-346-35-ubuntu-1404/)

Look at step #3.

---

### Post by fkervin on 2015-04-05
Many thanks to both for the answers.

I have install the nvidia drivers downloading the .run from its official site:

-Remove nvidia card and boot using integrated Intel.
-Download .run from nvidia site
-Rename the file to "nv.run" from its original name
-chmod +x the .run file
-Shutdown computer
-Plug nvidia card
-boot in safe mode, I get blank screen with cursor
-press CTRL+ALT+F1
-Enter username/pass
-run "sudo service lightdm stop" (If I don't do it I cant install nvidia drivers)
-navigate to folder containing the .run file
-run "sudo ./nv.run"
-Then the driver install althought it gives a warning message telling something about it's not in the operative system or something like this (sorry, I didn't took note).
-Restart

In this way everything seems to work ok, at least what I've try.

Should I install the driver in the way you told me instead this, ubunt72?

Many thanks again

---

### Post by ubunt72 on 2015-04-05
You could but I think when using Ubuntu, it's extra work because I think one of the most recent drivers is already packaged in Ubuntu.   I say this, because when I tried the live iso of Ubuntu Mate 15.04-beta2, I checked 'Addtional Drivers' and I could select, for e.g., 340 or 346.   I noticed that 346 and even 349 is in the list, too - if you check that one link I provided.   So, installing from the Nvidia site and running the -.run script shouldn't be needed.   You can try it if nothing else works, though.   However, as of this post, it gives the option of 343 and 346.  I could be wrong (maybe someone can confirm or correct me?) but I think that method (installing straight from the Nvidia site) means not using the ppa Ubuntu often uses with their video drivers.   Some users prefer not using the ppa, I think.  

346 is in Ubuntu 15.04, though.... See...
[https://launchpad.net/ubuntu/vivid/+source/nvidia-graphics-drivers-346](https://launchpad.net/ubuntu/vivid/+source/nvidia-graphics-drivers-346)

These instructions below should install 346.47 (not 346.16 as the link talks about - since, it's an outdated version):
[http://linuxg.net/how-to-install-the-nvidia-346-16-beta-driver-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/](http://linuxg.net/how-to-install-the-nvidia-346-16-beta-driver-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/)

Again, it's the edgers/ppa thing in Ubuntu.   They configure it their own way after they obtain it from Nvidia (I'm assuming) - it's just how they package it.

Edit:  If you did install it from the Nvidia .run script (the steps you posted), it's fine.   It will work.   I am not sure I recall correctly but I think you have to uninstall/remove that driver if you ever upgrade the main kernel and next time you upgrade the Nvidia driver, the Nvidia stuff needs to be uninstalled since there will be a mismatch with the new kernel and nvidia files (kernel etc.).    Anyway, don't worry about it for now. :)   I'm probably not explaining that accurately, anyway.

---

### Post by fkervin on 2015-04-16
> **ubunt72 said:**
> You could but I think when using Ubuntu, it's extra work because I think one of the most recent drivers is already packaged in Ubuntu.   I say this, because when I tried the live iso of Ubuntu Mate 15.04-beta2, I checked 'Addtional Drivers' and I could select, for e.g., 340 or 346.   I noticed that 346 and even 349 is in the list, too - if you check that one link I provided.   So, installing from the Nvidia site and running the -.run script shouldn't be needed.   You can try it if nothing else works, though.   However, as of this post, it gives the option of 343 and 346.  I could be wrong (maybe someone can confirm or correct me?) but I think that method (installing straight from the Nvidia site) means not using the ppa Ubuntu often uses with their video drivers.   Some users prefer not using the ppa, I think.  

346 is in Ubuntu 15.04, though.... See...
[https://launchpad.net/ubuntu/vivid/+source/nvidia-graphics-drivers-346](https://launchpad.net/ubuntu/vivid/+source/nvidia-graphics-drivers-346)

These instructions below should install 346.47 (not 346.16 as the link talks about - since, it's an outdated version):
[http://linuxg.net/how-to-install-the-nvidia-346-16-beta-driver-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/](http://linuxg.net/how-to-install-the-nvidia-346-16-beta-driver-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/)

Again, it's the edgers/ppa thing in Ubuntu.   They configure it their own way after they obtain it from Nvidia (I'm assuming) - it's just how they package it.

Edit:  If you did install it from the Nvidia .run script (the steps you posted), it's fine.   It will work.   I am not sure I recall correctly but I think you have to uninstall/remove that driver if you ever upgrade the main kernel and next time you upgrade the Nvidia driver, the Nvidia stuff needs to be uninstalled since there will be a mismatch with the new kernel and nvidia files (kernel etc.).    Anyway, don't worry about it for now. :)   I'm probably not explaining that accurately, anyway.

MANY thanks for your help, and sorry for taking so long in reply.

By now I'm going to leave this in the way I did, I don't know how to "activate" the integrated nvidia drivers when I replace the integrated intel with this one (I mean, system didn't boot.

Regards

---

