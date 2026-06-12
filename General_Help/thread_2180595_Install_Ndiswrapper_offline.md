---
title: "Install Ndiswrapper offline?"
date: 2013-10-13
forum: General Help
---

### Post by patrick20 on 2013-10-13
Well, my desktop has Ubuntu 13.04 installed and most everything is functioning properly except for my Wi-Fi. I have an Rosewill RNX-N250UBE USB wireless adapter. It picks up other networks perfectly however I cannot connect to them. The icon begins the animation like its connecting, but never actually connects, it just asks me for the password to my network, or if it's open it just says "Disconnected". 

I've already installed the website's recommended drivers for Linux and still nothing :/ I've read that people have gotten this adapter to work using Ndiswrapper, but I cannot install it because I don't have an internet connection on that computer. The LiveCD doesn't have ndiswrapper on it so I haven't a clue how to get ndiswrapper installed. Please help me thanks

EDIT:
I fixed this by downloading [this](http://packages.ubuntu.com/lucid/ndiswrapper-common), and installing my disk drivers for Windows XP. I have to use modprobe upon start up though. Thanks to all who were considering helping me! :D

---

### Post by Otto-C on 2013-10-14
This may point you in the right direction.

[http://www.ubuntuask.com/q/answers-modprobe-conf-options-not-loaded-on-startup-122906.html](http://www.ubuntuask.com/q/answers-modprobe-conf-options-not-loaded-on-startup-122906.html)

Also google "modprobe ubuntu startup" (without quotes) for more.
hth

Remember google is your best friend.  Also youtube has some great tutorials to
see how things are done.

---

