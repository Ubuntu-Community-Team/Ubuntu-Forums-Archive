---
title: "Wubi Installation Issue [Rev 459]"
date: 2008-03-28
forum: General Help
---

### Post by Termy58 on 2008-03-28
In installation I try to install, I'm at step 6/7 and it asks me if I want to import any documents. I didn't select any, the next button is unavailable for whatever reason. I select my user account still not available. I then proceed to press cancel because of the bug. Then I'm sent to Live Session User. Immediately I have no mouse, I'm highlight areas of the desktop to see where my mouse is, I go to install, and continue through as usual without a mouse. Then I pass step 6 perfectly without selecting the user. Then I get stuck at 15% (detecting file system)

EDIT

Forgot to mention

Windows XP Media Center
HP
Laptop touch mouse thing


Also I'm eating popcorn :popcorn:

---

### Post by ago on 2008-03-29
> **Termy58 said:**
> In installation I try to install, I'm at step 6/7 and it asks me if I want to import any documents. I didn't select any, the next button is unavailable for whatever reason. I select my user account still not available. I then proceed to press cancel because of the bug. Then I'm sent to Live Session User. Immediately I have no mouse, I'm highlight areas of the desktop to see where my mouse is, I go to install, and continue through as usual without a mouse. Then I pass step 6 perfectly without selecting the user. Then I get stuck at 15% (detecting file system)

EDIT

Forgot to mention

Windows XP Media Center
HP
Laptop touch mouse thing


Also I'm eating popcorn :popcorn:

[https://bugs.launchpad.net/wubi/+bug/205041](https://bugs.launchpad.net/wubi/+bug/205041)

---

### Post by dekarvn on 2008-04-03
I ran into the same problem
The solution doesn't solve it!!!

---

### Post by ago on 2008-04-03
You have to try latest Wubi (476) with latest daily ISO

---

### Post by arcadiano on 2008-04-04
I had the same problem with revision 479, I tried to install it from the live session, but when finally appears to be installed i have this problem: 

Ubuntu is loading, the suddenly appears another screen, then crashes, nothing happened after, this screen says:

> *Setting kernel variables...                        [OK]
/etc/rcs.d/s18mounthost: 68: awk: not found
/etc/rcs.d/s18mounthost: 68: awk: not found

*Checking root file system...
1195
fsck 1.40.8 (13-mar-2008 ) 
/dev/shm/root clean 108557/232000 files, 589529/927734 blocks [OK]

*Checking file systems...
1195
fsck 1.40.8 (13-mar-2008 )                [OK]

*Mounting local filesystems               [OK]

*Activating swapfile...                        [OK]
$Mounting securityfs on /sys/kernel/security: done
Loading AppArmor profiles: done

*Checking minimum space in /tmp... [OK]


and then... nothing more, only a cursor flashing in the left corner...

---

### Post by ago on 2008-04-04
can you run wubi installer (windows side) and send me the preseed.cfg file (deleting the password) BEFORE rebooting?

When rebooting, press esc and select "VERBOSE MODE".

If you get stacked installing, from the live desktop, zip /var/log/ and post it here

---

### Post by arcadiano on 2008-04-04
here is my preseed.cfg file, I did't see any "verbose mode" maybe because it's in spanish? i'll try in english, anyway i installed from live session again and i had the same problem, it never loads

EDIT: Tried in english but the menu is still in spanish, I tried to install in english but as you said the installation didnt work... here is my /var/log/ zip

---

