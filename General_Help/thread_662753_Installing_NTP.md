---
title: "Installing NTP"
date: 2008-01-09
forum: General Help
---

### Post by miqie on 2008-01-09
I just installed Ubuntu 7.10 on my computer.  I wanted to set my clock to synchronize with the internet servers.  When I change to that option I get the message that NTP is not installed, so I click the button to do that, but nothing changes.  I then entered: " sudo apt-get install ntp"  in the terminal window and got the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ntp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ntp has no installation candidate

What are my options now?  :confused:

---

### Post by taurus on 2008-01-09
Check to make sure you have all the repos available in /etc/apt/sources.list.

Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line to comment out the cdrom.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close gedit windows.  

Then run

```
sudo apt-get update
sudo apt-get install ntp
```

---

### Post by miqie on 2008-01-09
I did exactly as you suggested and...........................................IT WORKED! Much thanks to you!  I am an absolute newby at Ubuntu and using the command line etc.  I come from XP country where just about everything is done by mouse.  Its fun learning new things! :KS

---

