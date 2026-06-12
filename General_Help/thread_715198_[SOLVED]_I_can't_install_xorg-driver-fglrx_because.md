---
title: "[SOLVED] I can't install xorg-driver-fglrx because it is missing from Synaptic Packag"
date: 2008-03-04
forum: General Help
---

### Post by xOrangeFirex on 2008-03-04
I was having trouble with nicotine that I could not get fixed. I needed nicotine because I couldn't figure out amule and I needed a P2P program. So I just reinstalled Ubuntu 7.10 entirely from scratch. I am far from a pro with ubuntu, but I know how to get everything essential working (java, restricted drivers, etc). Now I go into Synaptics Package Manager to install some of the required xorg-driver-fglrx (so I can get my ATI video card working) and other things. When I get in there I find that almost all the packages were installed (there was a total of 1132 packages and 33 not installed) As I recall (before the reinstall) there were more than 20000 packages total. I then assumed that pushing refresh would get me all my packages. This didnt work. I gave up on that and went to try to install java and other necessary programs from add/remove. I tried to check the box and it said:
 "The list of applications is not availabe(typo in ubuntu)

Click on 'Reload' to load it. To reload the list you need a working internet connection."
This happened every time I tried to install something. So I then gave up on that. Next I went to get my updates and as I recall there was more than 180 from the last time I installed linux so I was ready for a long wait. I got there and it said my computer was up to date even though I had just installed the OS. I really have no idea where to go from here. I really need some help. Thanks in advance.

---

### Post by taurus on 2008-03-04
Sounds like you don't have enough repos enable in /etc/apt/sources.list.  In Add/Remove, click Preferences and make sure there is a check mark in front of the first four lines except the last one, Source code, and the Cdrom in the window below.  Close and and click Make Changes, bottom right of the Add/Remove window.  Now, see if you can install anything this time.

---

### Post by xOrangeFirex on 2008-03-04
I figured it out. All that I needed to do was go into software sources and check all 5 boxes. Then I could go and it would reload properly. Thank you though.

---

