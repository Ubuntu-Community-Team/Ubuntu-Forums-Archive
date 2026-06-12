---
title: "Canon printer install help"
date: 2008-01-16
forum: General Help
---

### Post by andypeter on 2008-01-16
I have a canon IR3530 and found a canon driver that is supposed to work with linux systems.  I got the printer to make noise and then come up with an error, and then I found this page: [http://dalbrizio.googlepages.com/how-to_#sque](http://dalbrizio.googlepages.com/how-to_#sque) .  

I followed the steps and it still didn't work.  The last step says to "tail -f /var/log/syslog" and search for lines tagged "audit"."  

I did that and found the line with "audit", and got this: 

"Jan 16 09:16:04 andy-laptop kernel: [  992.682609] audit(1200492964.222:7):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=11880 profile="/usr/sbin/cupsd" 

I do not know how to do this last line of the instructions: 
"And modify /etc/apparmor.d/usr.sbin.cupsd accordingly."

Could someone please help me get this printer to print?  I would appreciate all the help! :)

---

### Post by veloce on 2008-01-16
I originally followed these instructions:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

But they are a bit out of date.

The driver I have supports your printer so you should go to the Canon site and download it. It includes rpm and deb packages and a comprehensive installation manual. Note however that the debs don't work under Ubuntu (wrong version of cups lib).

The package I downloaded was called pslinuxv140.zip

Unpacking it gives 32 bit and 64 bit directories each containing a cups common and cups ps3 file.

use alien on the rpm packages to get debs that work with ubuntu:

sudo alien *.rpm

(ignore the "script" warning)

Install the common file first then the other.

Now use System - Administration - Printing to install a new printer.  When asked for the model, use the ppd button.

PPD files are stored in /usr/share/cups/model

for the ir3530 you want CNCUPSIR3530SK.ppd

Good luck.

---

### Post by zionpsyfer on 2008-01-16
It's not much help, but I had a heck of a time trying to get cupsd working with apparmor running.  In the end I just disabled apparmor to get it working.  If you don't feel you need apparmor, this might be the best way to go.  If you do.... then, sorry for not being much help. ;)

---

### Post by andypeter on 2008-01-17
Dear Veloce,

Thanks for all the help!  I am going to restart and see if it worked.

Thanks,
Andy

---

### Post by andypeter on 2008-01-17
Volce,

I followed all your instructions but now after having both packages installed and restarting, the printer won't even make a noise like it used to followed by a series of error beeps.  I checked the printer and in the log it does show the print job but then has next to it "NG" meaning "No Good" (according to Canon).  It doesn't give a lot to go on...

I don't know if there is a setting I need to change or what.  Do you have an idea what this problem is due to?

Thanks again for your help!

---

### Post by andypeter on 2008-01-17
I pulled out the manual and looked up the error code #853 and it said there are two reasons for it not printing: 

1) When trying to print a large number of pages, the job is not performed due to insufficient memory resources. 

2) The job could not be processed, because it was canceled from the printer driver while print data was being sent to the machine.

The first option is probably not the problem. It was one page of text I was trying to print.  The second option I have no idea what to do in order to fix.

Thanks for any and all help!

---

### Post by firmit on 2008-02-20
I need help! Jeez

First - I followed the instructions - 100%!
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

But when I check if the printer is ready with:

$ captstatusui -P LBP2900
I get:
*** captstatusui Socket Error ***

What is the problem?? Need help!

Added: I should add I only found the 1.6 version capt file. This includes a .deb file.

---

### Post by Bizigo on 2008-02-29
I have the same problem as FIRMIT after having done a reinstallation of UBUNTU. I succeeded before but now it fails and I don't find any solution.

Thank you for your help.

---

### Post by shadowtroopers on 2008-03-02
i think you can go to this site

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

---

### Post by firmit on 2008-03-05
Using the "old" 1.3 driver worked. I found a backup on my laptop.
However, I am still wondering why the 1.6 driver is not compatible.

---

