---
title: "Trouble starting X, insufficient memory?"
date: 2012-11-03
forum: General Help
---

### Post by krishnamohan on 2012-11-03
Hi...

Yesterday, I added a network printer at my institute. While trying to print for the first time, the computer asked for authentication, then complained of low disk space. I deleted a 3 GB movie from the Desktop and restarted the computer.

Now Gnome does not start.

I first got  a screen which said something like "Starting cups server.." at the end.
I went back and deleted all the files that had been created recently in /etc/cups/.   
Now the screen says that it is starting GDM, then stopping GDM and the last message is something like "Stopping Jupiter dameon..".

I could drop to the command line and login....a "df -h" showed that the usage in "/" is 100%. I deleted some 3 GB of files from /home. Now "df -h" shows 3 GB  difference between total space and available space but the usage is still listed as 100%

I tried "startx"....I get a blank screen ...dropping to command line, I see the following messages...

fglrx: No matching device section for instance (BUSID PCI:0@1:0:1) found
Waiting for X server to begin accepting connections...
No protocol specified...
No protocol specified...

If I login as root, am able to start X, but the screen just shows a completely empty desktop.....am unable to do anything....

---

### Post by pqwoerituytrueiwoq on 2012-11-03
look for over-sized (measured in GB) log files in /var/log/
BTW memory=RAM not HDD

---

### Post by krishnamohan on 2012-11-03
Hi..

Tried that...no GB files..deleted some MB files...now the total size is only 16 MB.....but it is still not starting...
df -a still gives me 100% usage.

---

### Post by pqwoerituytrueiwoq on 2012-11-03
try looking in sub folders
can you install bleachbit?
```
sudo apt-get clean;sudo apt-get install bleachbit
```what does this give you
```
lspci | grep VGA
```just need what is after the colon, you may need to reinstall your gpu driver

---

### Post by krishnamohan on 2012-11-06
Well...right now I am not able to connect to a network in ubuntu...so I cant install belachbit using sudo apt-get...am working on getting the net back...

Here is what I get from the lspci command:

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]

---

### Post by krishnamohan on 2012-11-07
Also..now I have an ubuntu usb livestick.....would that be of any help?

---

