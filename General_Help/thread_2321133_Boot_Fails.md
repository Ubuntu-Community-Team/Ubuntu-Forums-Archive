---
title: "Boot Fails"
date: 2016-04-20
forum: General Help
---

### Post by Otto-C on 2016-04-20
Ubuntu 12.04.5 fully updated.
A dual boot machine with windows Xp.
My friend apparantly from the Grub menu booted the machine
to recovery mode. He apparantly clicked on a couple of item
unale to inform me which. When he got to a place he could
boot the machine it got to the Ubuntu screen with the five
dots and at the point where it activates/recognizes the printer
it goes no further.
I duplicated his findings and came away with a couple of notes
that may help. I did DPKG and FSCK.
I believe it was DPKG showed:
Unmet dependencies linux headers 3.2.0-101 Generic but is not installed.
linux headers generic-pae: Depends linux headers-3.2.0.101-generic-pae
but is not installed.
E: UNMET dependencies. Try using -F
(did not understand how to use command.)
Some how got a screen that showed dialog box saying
Could not UPDATE ICEauthorityfile
/home/greg/.greg/ICEauthoritylogout
This show a login screen.
Entered Greg password and it comes right back to this screen
Tried it for the Guest session  same result
Any help appreciated.
otto-c

---

### Post by oldos2er on 2016-04-20
From within recovery mode you will need to enable networking, then drop to a root shell prompt and try ```
apt-get install -f
``` to fix dependencies.

---

### Post by oldfred on 2016-04-20
If you can boot to terminal, you can try this to reset ownership & permissions.
Thread is old , but error seems to be same.

 .ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)

---

### Post by Otto-C on 2016-04-26
Sorry for delay reporting progress. Sickness in friends house.
Did the following:
# apt-get install -f
w: Not using locking for read only lock file /var/lib/dpkg/lock
e: Unable to write to /var/cache/apt/
e: The package lists or status file could not parsed or opened.

What next?
Thanks
otto-c

---

### Post by oldfred on 2016-04-26
Are you in terminal in your install or live installer?

If in terminal you need sudo.

Or lock file is open because you have another process using it. 
I get that when I leave synaptic open but try to run some update in terminal. Or forget sudo.

---

### Post by Otto-C on 2016-04-26
I believe install. Booted from safe mode. Then selected root. So I was now
# apt-get install -f.  And got the above message.  I also did # sudo apt-get install -f with the same result.  Have briefly tried to get to $ but cannot. 
Typing # exit returns safe mode menu.

Thanks
otto-c

---

### Post by oldfred on 2016-04-26
If you have rebooted there should be no lock.

 sudo apt-get install -f
Locked dpkg - only if sure you are not running another update.
sudo lsof /var/lib/dpkg/lock
if another process has lock then you can sudo kill (process #)
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

---

### Post by Otto-C on 2016-04-29
Thanks for helping.
Finally got to login prompt . At the terminal prompt ($) tried
all of suggestions and received numerous err messages as well
as no space left on device. Similar message doing them from root
(#).
Going to do a full install.
Thanks again,
otto-c

---

