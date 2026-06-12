---
title: "Setting hard drive spin down time?"
date: 2013-04-25
forum: General Help
---

### Post by icanjam on 2013-04-25
I'm not sure what the default timing is but I know that's what I'm using. This computer runs 24/7, so I'd like to hard drive to spin down when I'm at school, or sleeping. I don't really understand how the hdparm works. How would I go about making it spin down after say, 3-4 hours?
Just updated to xubuntu 13.04 today by the way.

---

### Post by icanjam on 2013-04-25
Actually I think I got it I ran 
gksudo gedit /etc/apm/event.d/20hdparm
then edited APMD_SPINDOWN18
to
APMD_SPINDOWN2880 which I believe ends up as 4 hours. (number of seconds divided by 5)
Then I went back into the power manager and checked the "spin down hard drives" box.

---

### Post by efflandt on 2013-04-25
man hdparm

You probably want the -B  switch for hdparm. But note that any drive logged to will wake up for any logging, so it is normally only useful for drive(s) you are not running from, or if you totally disable logging (which may leave you wondering what went wrong if something does).

Whenever I tried to use Ubuntu system settings in an earlier version to try to spin down my main drive when running from SSD, it did not seem to do anything.

You never know how long a drive is going to last. The 3 year old drive on my current system that runs constantly occasionally remounts read only (I have a replacement drive that I need to copy over to). But an old Celeron 300 in my basement has drives that have been running for 10 years or longer, including non-stop 5 years without booting between long power failures.
```
efflandt@realhost:~> ls -l /etc/*release*
-rw-r--r--    1 root     root           36 2003-03-18 11:48 /etc/SuSE-release
efflandt@realhost:~> cat /etc/*release*   
SuSE Linux 8.2 (i586)
VERSION = 8.2
```

---

### Post by icanjam on 2013-04-26
> **efflandt said:**
> 
any drive logged to will wake up for any logging

I've never been so great with Linux but basically your saying that it'll just spin back up from just running the OS anyway?

---

### Post by Impavidus on 2013-04-26
Occasionally some things may be logged. But why not save some trees and completely suspend the computer if you don't expect it to do anything? Except for web servers and the like there aren't many computers that need to tun 24*7. As you say, you think you can spin down the drives, so do don't expect your computer to do anything whilst you are sleeping. There even exists such a thing as wake-up from LAN.

---

