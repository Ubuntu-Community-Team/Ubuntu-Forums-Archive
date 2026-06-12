---
title: "restoring sudo root ownership in /usr/bin/"
date: 2013-06-30
forum: General Help
---

### Post by dragonfly41 on 2013-06-30
I'm running a dual boot laptop.   Ubuntu 12.04 as primary OS and Windows Vista as secondary OS.

   In Ubuntu I blundered and applied this command to /usr/bin/


   $ chown -R <username>:<username> /usr/bin


   This mistake arose from editing and saving some files in Krusader root mode terminal and I needed the files to be at user permission.

   The net effect is that I lost sudo in /usr/bin/sudo .. and from reading about the subject I will have lost other permissions in /usr/bin/

   I see this error ...  "sudo must be setuid root".


   I read a few threads and one recommendation  was to reboot into recovery console and in root shell apply these commands:


   chown [root:root]("http://ubuntuforums.org/root/root.html") /usr/bin/sudo
chmod 4755 /usr/bin/sudo


    So I tried this but got this ...


   chown [root:root]("http://ubuntuforums.org/root/root.html") /usr/bin/sudo
chown: changing ownership of /usr/bin/sudo: read-only file system

   chmod 4755 /usr/bin/sudo
chmod: changing permissions of /usr/bin/sudo: read-only file system

   
but when I ran command

   $ ls -l /usr/bin/sudo

   there was no change seen to ownership.


   I've tried booting up an old USB version of ubuntu 12.04 and also a live CD so that I might hack the usr/bin properties.

But when I switch to either USB boot or CD boot the Grub menu stubbornly comes up and my Live CD doesn't boot up.   So for some reason I can't boot up Live CD (CD or USB). 

 I'll keep trying that option so that I can change properties of /usr/bin from external OS.


   The only other route into the internal Ubuntu file system is via Vista in my dual boot setup. 
  But ext file systems can only be read from Windows (as far as I know).


   Is there any other way of repairing /usr/bin/sudo to have root ownership .. or is this leading to a reinstallation?

---

### Post by cool110 on 2013-06-30
Recovery mode defaults to mounting / as read-only. you need to remount it before you can change permissions.
```
mount -o remount,rw /
```

---

### Post by dragonfly41 on 2013-07-01
Thanks .. that additional mount command allowed me to restore sudo root permissions through recovery menu.

But the question now is how many other files in /usr/bin/ must be restored to root:root?

And how do I find out which files must be root:root .. or other permissions?

I am now able to launch a VirtualBox image of ubuntu 12.04 (from VirtualBox in my desktop ubuntu 12.04) and I can inspect the /usr/bin/ folder in the VM.   I can see that most in /usr/bin/ are root:root.

So is it safe to now change files recursively .. only in /usr/bin/ .. back to root:root permissions in my desktop ubuntu?

sudo chown -R root:root /usr/bin/

---

### Post by Impavidus on 2013-07-01
Luckily you didn't do a chmod, only a chown. A quick check on my 12.04 systems shows everything in /usr/bin is owned by root:root except```

-rwsr-sr-x 1 daemon daemon     42800 okt 25  2011 at
-rwsr-xr-x 1 root   lpadmin     9768 mei 13 15:09 lppasswd
-rwxr-sr-x 1 root   crontab    34776 jun 19  2012 crontab
-rwxr-sr-x 1 root   mail       13932 okt 17  2011 dotlockfile
-rwxr-sr-x 1 root   mlocate    34432 aug 17  2011 mlocate
-rwxr-sr-x 1 root   shadow     18120 sep 12  2012 expiry
-rwxr-sr-x 1 root   shadow     45284 sep 12  2012 chage
-rwxr-sr-x 1 root   ssh       128416 apr 11 09:27 ssh-agent
-rwxr-sr-x 1 root   tty        18036 mrt 30  2012 wall
-rwxr-sr-x 1 root   tty         9728 mrt 31  2012 bsd-write
-rwxr-sr-x 1 root   utmp      365260 jun  6  2011 screen
-rwxr-sr-x 3 root   mail        9684 okt 18  2011 mail-lock
-rwxr-sr-x 3 root   mail        9684 okt 18  2011 mail-touchlock
-rwxr-sr-x 3 root   mail        9684 okt 18  2011 mail-unlock
```

---

### Post by dragonfly41 on 2013-07-01
Thanks for that exception list .. I've already changed all /usr/bin/ to root:root and I'll now run through your list to tweak my permissions.

A huge sigh of relief that I didn't apply chmod but only chown.

On doing further reading ..

 [http://unix.stackexchange.com/questions/16962/how-to-get-back-sudo-on-ubuntu](http://unix.stackexchange.com/questions/16962/how-to-get-back-sudo-on-ubuntu)

   
"apparently running chown breaks setuid and setgid bits, so you will need to manually 
compare to an existing system to restore all of those once you fix the ownership again"

---

### Post by Impavidus on 2013-07-01
The other files that have the setuid or setgid bits set on my installation are```

-rwsr-sr-x 1 root   root        9524 jan  3 16:24 X
-rwsr-xr-x 1 root   root       13860 nov  8  2011 arping
-rwsr-xr-x 1 root   root       14012 nov  8  2011 traceroute6.iputils
-rwsr-xr-x 1 root   root       18104 mei 17  2012 pkexec
-rwsr-xr-x 1 root   root       30896 sep 12  2012 newgrp
-rwsr-xr-x 1 root   root       31748 sep 12  2012 chsh
-rwsr-xr-x 1 root   root       40292 sep 12  2012 chfn
-rwsr-xr-x 1 root   root       41284 sep 12  2012 passwd
-rwsr-xr-x 1 root   root       56208 jul 28  2011 mtr
-rwsr-xr-x 1 root   root       57956 sep 12  2012 gpasswd
-rwsr-xr-x 2 root   root       69708 feb 27 20:32 sudo
-rwsr-xr-x 2 root   root       69708 feb 27 20:32 sudoedit
```

Your contents of /usr/bin will differ, as you'll have other applications installed, but few of them will use other ownership/permissions. Those are mostly the administrative programs, or some games that keep global score files (but those are in /usr/games).

---

### Post by dragonfly41 on 2013-07-01
To close this thread for information I'm adding this useful introduction to setting .. SUID, SGID etc.

[http://www.linuxnix.com/2011/12/suid-set-suid-linuxunix.html](http://www.linuxnix.com/2011/12/suid-set-suid-linuxunix.html)

Thanks.

---

