---
title: "configure HP printer on ubuntu 20.04 LTS dont work"
date: 2022-09-09
forum: General Help
---

### Post by sir.Evan on 2022-09-09
(the printer worked fine under Ubuntu 22.04 LTS but there was so many other errors that I gave up using that distribution.)
After having installed Ubuntu 20.04 and updated the software and installed hplip-3.16.7 and connected the printer with a usb cable and run this command to identify the printer with this command
hp-setup -b usb

no printer can be found!!!!!!  is shown on the screen.
there was an attribute error: module 'platform' has no attribute 'dist', earlier in the installation.
;could that be the error???

what can I do to get the printer working???? please help

I have tested the printer and cable on a windows pc and the printer is working.
The ubuntu 20.04 LTS was installed recently due to problems with 22.04.

;i forgot to mentioned the printer i use;
it is a HP deskjet 2320 usb printer

---

### Post by MAFoElffen on 2022-09-09
HP, Canon and Epson printers are usually a given on Linux and cups.

You never mentioned which printer it was... Could you please post the printer model?

---

### Post by sir.Evan on 2022-09-10
sorry, 
it is a HP deskjet 2320 usb printer

---

### Post by aljames2 on 2022-09-10
I had the same issue a while back for strict USB printing on my HP.  Not sure why because I have had other HP printers that worked straight away.  But for my current HP, the problem existed on both my KVM host machine (MATE), & a guest VM running Ubuntu 20.04 desktop.  Read through this for possible solution.  In short I had to remove the ippusbxd package, then physically unplug & reattach the USB cable before running another simple scan.

[https://askubuntu.com/questions/1258462/ubuntu-20-04-simple-scan-does-not-detect-scanner](https://askubuntu.com/questions/1258462/ubuntu-20-04-simple-scan-does-not-detect-scanner)

---

### Post by sir.Evan on 2022-09-11
Thank you [https://ubuntuforums.org/member.php?u=2118065](https://ubuntuforums.org/member.php?u=2118065)  for your reply

I only did this command used by jimmy-widdle

sudo apt purge ippusbxd

reconnected the printer with usb cable and ran the command

hp-setup -b usb

no printer was found!!!!

I sure have to do something more but I need some more help please.:o

---

### Post by sir.Evan on 2022-09-11
I had a look on the system whether hplip was still there

dpkg -l hplip
ii hplip  3.20.3+dfsg0-2 amd64

it seems to be there but with a newer version i think ???? still not working though:(

---

### Post by sir.Evan on 2022-09-11
I had another look for my printer , with no luck unfortunately, but some overseen info was show:

evan@evan-Lenovo-ideapad-110-14IBR:~$ hp-setup -b usb


HP Linux Imaging and Printing System (ver. 3.20.3)
Printer/Fax Setup Utility ver. 9.0


Copyright (c) 2001-18 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb


Done.
-----------------------end of copy
 
the response is very different from my first attempt so something is definitely missing , but what????

sorry to so useless.

---

### Post by aljames2 on 2022-09-11
If you clean up your original post so others can read it more easily you may get more responses.  Not sure why your OP has all those line break tags & other junk in it.

Not sure what else could be going on with your printer not being detected.  You could also try:

- updating your 20.04 OS.  
- Power off the printer
- unplug usb cable
- restart computer
- plug in usb cable
- power on the printer, give it time to make its noises as it powers on
- go into your desktop settings in the printer section and try to add a printer

These are just basic steps to try to make sure it’s not some funky issue where the printer won’t wake up or some other physical connection problem.

These printers should just work when you plug them into Ubuntu.  I have never had to install the manufacture drivers or other third party software in order for a printer to work and scan and do whatever else I need.

---

### Post by sir.Evan on 2022-09-11
hi Aljames2,

thank you for your advice
I dont know how the mess in my post happened. I will try to clean it up or start over.

---

### Post by sir.Evan on 2022-09-11
hi Aljames2,

thank you for your advice
I dont know how the mess in my post happened. I will try to clean it up or start over.

---

### Post by sir.Evan on 2022-09-11
[COLOR=#000000]hi Aljames2,

i followed your advice and got the printer working.

I think i have confused everybody.

should i delete the whole thing or what???
[/COLOR]

---

### Post by sir.Evan on 2022-09-11
i edited the introduction mess but i can see it didnt change .

how do i close or delete this embarrassing mess?????

---

### Post by aljames2 on 2022-09-11
Glad you got it working.

Just edit your original post and use the thread tools to mark it as ”Solved”

---

