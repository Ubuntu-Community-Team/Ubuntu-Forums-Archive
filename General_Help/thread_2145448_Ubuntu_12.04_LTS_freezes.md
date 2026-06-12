---
title: "Ubuntu 12.04 LTS freezes"
date: 2013-05-15
forum: General Help
---

### Post by Silent Hill on 2013-05-15
Hello to everyone!
it's been happening for about 2 weeks that ubuntu (installed on a laptop sony vaio sve1513q1es) randomly frezees (mouse and keyboard are blocked, I can't switch to alt+ctrl+f1 and nothing else...the only thing I can do is turn off the pc brutally).
I've been trying many things:
first of all even if my computer is a 64 bit I installed the 32 bit version (because there were some unknown problems with 64 bit cd installation)...
could this be a problem?
Thus, I avoid using the -pae kernel and I'm actually using 3.2.0-41-generic.
I thought the problem was the wifi device (I have another sony pc where wifi device created problems) and so everytime I turn on the pc I perform:
sudo iwconfig wlan0 power off
and I installed the wireless backported drivers.
but this doesn't solve the problem either...
Then I read that google chrome browser causes the pc to freeze and so I uninstalled it.
The results are that my laptop seems to work correctly only with 3.2.0-41-generic and mozilla firefox.
Moreove using the newest kernel pae it blocks...both with google chrome and without google chrome.
So...what I can do to solve all this?
I'd really like to use Chrome because I'm developping a GWT aplication and I would prefere to use Chrome instead of Mozilla...
and why can't I use the pae kernel? (for ezample linux-image-3.2.0-42-generic-pae)
Please, if you can help me I would be very grateful to you!

---

### Post by Silent Hill on 2013-05-16
up

---

### Post by fantab on 2013-05-16
The simplest and cleanest solution will be to install Ubuntu 12.04 64bit. 

Simply put, PAE kernel is for 32bit systems with more than 4GB RAM. Your system is not 32bit. (I think 12.04.2 version comes with this PAE Enabled and not the earlier  versions. So if you have installed 32bit 12.04 or 12.04.1 then that  could be an issue, I am not cent per cent sure though).
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)
[https://en.wikipedia.org/wiki/Physical_Address_Extension](https://en.wikipedia.org/wiki/Physical_Address_Extension)

What kind of problems you had with 64bit? Try to install 64bit again and tell us what problems you have, so we can help you install 64bit.

---

### Post by Silent Hill on 2013-05-16
I understand...the problem is that I can't install ubuntu 12.04 64 bit because actually I'm working on a big java software and I have a very complex development enviroment with many libraries...for the moment I have no time to waste on reinstalling and reconfiguring everything so I w

---

### Post by Silent Hill on 2013-05-16
I understand...the problem is that I can't install ubuntu 12.04 64 bit because actually I'm working on a big java software and I have a very complex development enviroment with many libraries...for the moment I have no time to waste on reinstalling and reconfiguring everything so I would prefere another kind of solution if possibile...

About the cd, it just showed the ubuntu logo and then it all stopped...I burnt it twice with no chanfes :(

---

### Post by Silent Hill on 2013-05-16
But even if I'm forced to use the generic version (not the pae) it's not a problem for me...the most annoying thing is google chrome. I've been using ubuntu for more than 5 years and I've never had problems with it...I would like to solve this one because I've been developping a GWT application and it'd be better for me to test it with google chrome rather than with mozilla...

---

### Post by fantab on 2013-05-16
Why cant you use Chromium, instead of Google Chrome?

---

