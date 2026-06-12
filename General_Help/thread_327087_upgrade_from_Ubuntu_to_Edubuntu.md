---
title: "upgrade from Ubuntu to Edubuntu?"
date: 2006-12-28
forum: General Help
---

### Post by M8M on 2006-12-28
Hi, 

I would like to use the school tools and calendars from edubuntu to home school my children. I am in the process of installing edubuntu on their computer, but I currently have ubuntu on my computer. Can I use the school tools on my ubuntu without switching to edubuntu on my computer? (If so, can I have a step by step of how to do that? I know NOTHING about installing anything. I have done some installing step by step, but I don't understand what I'm doing really.)
If I can't use them, how do I switch to edubuntu on my computer, without completely reinstalling and erasing everything I have on ubuntu? 
Is there someone out there with a bit of time and knowledge of the school tools that could walk me through setting it all up?

I know it's a lot to ask, but this is a great community and I hope some one can help.

Thank you.

M8M

---

### Post by k1001001 on 2006-12-28
You can do either one you like. You can download the educational programs into normal Ubuntu, or you can just as easily install Edubuntu and keep normal Ubuntu at the same time. Edubuntu is a desktop environment, not really a whole other operating system, as I would understand it. Switching from Ubuntu to Edubuntu will keep all of your files and keep normal Ubuntu intact as well, so you don't have to delete anything, and you aren't losing anything. Switching desktop environments is really easy. I just did this last night, and I'm surprised as to how well it works and how easy it was.

To install Edubuntu, do the following.
1. Go to Terminal and type: ```
sudo aptitude install edubuntu-desktop
```
2. This will be a rather long download and install process, but it will do it automatically on its own. You can work on something else while this is going on. When it is done installing, click the Power button at the top right, and select "Log Out."
3. At the Ubuntu log-in screen, select "Session" and then "Edubuntu" (or whatever isn't Gnome. Gnome is what you have now.).
4. It will ask you if you want to run Edubuntu as your default environment, or just for this session. Click "Just For This Session" (unless you want it as default), and then Edubuntu will load.

All of your files will still be there, and it will come with the Edubuntu programs installed as well.

If you don't want to install Edubuntu, and would rather download the educational programs to normal Ubuntu instead, check out the Add/Remove Applications program. Go to the Applications menu at the top left, then select "Add/Remove Applications." There, you will see an icon on the left of the window saying "Education." Click that, and a list of educational programs available to download will be on the right, with a full description of each one.

Either one will work just fine. I just wanted to stress that installing Edubuntu won't delete or reverse anything that you've done so far on normal Ubuntu. You can have both Ubuntu and Edubuntu, and use whichever one you like at any time.

If you want to remove edubuntu (in case you don't like it), go back to normal Ubuntu (Gnome) and type this in the terminal:
```
sudo aptitude remove edubuntu-desktop
```

---

### Post by M8M on 2006-12-28
Thank you for your help. I tried and ran into this error:
:~$ sudo aptitude install edubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  wine
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base

Can you suggest anything to solve this?

Thank you.

---

### Post by k1001001 on 2006-12-28
I've got no idea honestly. Maybe try:
```
sudo aptitude update
```
and then run the install line again.

If that doesn't work, hopefully someone else will answer this thread. I just started in Ubuntu/Linux a couple of months ago, so my knowledge is pretty limited. Sorry it didn't work out for you!

EDIT: It looks like you have an anti-virus program installed, and that is getting in the way of you installing Edubuntu. Try installing something else like Google Earth (sudo aptitude install googleearth). If it does the same thing, then your anti-virus may be blocking you from installing programs.

Have you installed programs before using aptitude? Maybe try installing Edubuntu using "sudo **apt-get** install edubuntu-desktop".

I hate to say this, but do you think an anti-virus is necessary? An extremely low amount of viruses have any success running in Linux.

---

### Post by dothedorky on 2006-12-28
You also might want to try upgrading your system.

sudo aptitude-get update
sudo aptitude-get dist-upgrade

and then try installing edubuntu's desktop as mentioned above.

---

### Post by M8M on 2006-12-28
ok, I'm not aware of having installed any anti-virus on ubuntu/edubuntu. Howeer I have a dual boot and the windows partition has an anti-virus on it. I hope that they are not interfering with one another.

I tried the updating and the first one worked fine, but the second one listed the following error:sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  wine
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

so I'm back to the same problem. Could it be that the wine is interfering and that I need to uninstall it first? If so how do I do that?

Thank you for your help! You guys are great, even if newbies like me! ;)
M8M

---

### Post by k1001001 on 2006-12-28
The reason I said your computer appears to have an anti-virus is because of the line mentioning "/var/run/clamav." When I Googled it, results came back talking about the [Clam Anti-Virus program]("http://www.clamav.net/"). It's weird that wine pops up as well, though. Try re-installing Wine, or perhaps removing Clam AV.

To re-install Wine, first remove it:
```
sudo aptitude remove wine
```
Then reinstall it:
```
sudo aptitude install wine
```
If you have the same errors, try using apt-get instead of aptitude:
```
sudo apt-get remove wine
sudo apt-get install wine
``` 

If this doesn't work, then try removing the Clam Anti-Virus. Or just remove it anyways, since you probably don't need it:
```
sudo aptitude purge clamav
```
And again, if this causes an error, try using apt-get instead of aptitude:
```
sudo apt-get remove clamav
```

Post back with the results. I hope this makes some progress.

---

### Post by M8M on 2006-12-28
I searched the forums for the clamav-base error and found that the advice was to uninstall, then reinstall it. I did so and it solved the problem.

I have switched to Edubuntu now but want to know how to set up the school tools applications.

Thanks,

---

