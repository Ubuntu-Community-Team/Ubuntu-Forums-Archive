---
title: "Setting system date and time affecting the clock and date on BIOS"
date: 2007-09-20
forum: General Help
---

### Post by satimis on 2007-09-20
Hi folks,


Ubuntu 7.04 server amd64


Sometime strange happened here.  Running "date -s ...." to set date and time of the system affecting the clock and date on BIOS.


The story is as follow;

Recently the date and time on the system was not correct.  I changed a new battery and reset everything.  Each day after booting the PC I have to run "date ..." to reset the time.


Just made following test

Booted the PC and entered BIOS page.  It was found;

System Time 4 6 21
System Date  Fri Sep 21 2007

reset them and exited BIOS setup.  Rebooted PC and entered the BIOS page again.  The date and time there was found correct.  Reboot the PC checking it twice.

Then rebooted PC and login as user.  Ran "sudo reboot" to reboot PC.  Entered BIOS setup page and found the time and date being correct.

Rebooted PC again and login as uesr.  

Ran;
$ sudo date -s "09/20/2007 xx:xx:00" 
to adjust date and time

Then;
$ sudo reboot
to reboot the PC

Entered BIOS setup page.  It was found that the time was reset as;
System Time 4 6 21
System Date  Fri Sep 21 2007

I checked it at least 3~4 time.  If I did not change the system date and time, the time and date on the BIOS did not have problem.  The time was running.

I don't know why changing the system date and time will affect the clock and date on the BIOS bringing it back to the same wrong time.

Please advise where shall i check.  TIA


B.R.
satimis

---

