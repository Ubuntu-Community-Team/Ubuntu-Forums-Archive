---
title: "'dpkg --configure -a' error"
date: 2007-01-02
forum: General Help
---

### Post by meleeglow on 2007-01-02
I just downloaded 'ubuntu-6.10-desktop-I386.iso'(just so you know the version I used), I am new to linux and OS installation altogether, but I just put ubuntu on a spare drive I had laying around, the master came with the budget PC I put it in. Anyways I am having trouble getting the scheme of the os so I went to add and remove programs, and was playing around in there for a while installed a few things, then I tried the "Achilles Life Simulator" and it froze up. After I shut it down to reboot I tried to get XChat IRC. clicked apply twice then I got an error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " so after doing a few educated guess to what it meant I opened the "Terminal" and entered 'dpkg --configure -a' (w/o quote) and it told me dpkg: requested operation requires superuser privilege.
> meleeglow@meleeglow-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

So  I logged in the console(Ctrl+Alt+F1),used my account the only account I know of on this OS(unless there is a default admin I don't know?) and got the same message 
> meleeglow@meleeglow-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

I don't  know what to do after runinng that like I did or how to do it right. any help would be great but please understand that I am new to the OS so it would help if it was step by step.

---

### Post by haiku99 on 2007-01-02
use **sudo** in front of any command that requires super user...

---

### Post by meleeglow on 2007-01-02
Okay I got this:> dpkg: error processing achilles (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 achilles


how do I reinstall it

---

### Post by meng on 2007-01-02
Try
sudo apt-get remove achilles

---

### Post by meleeglow on 2007-01-02
Got this

> meleeglow@meleeglow-desktop:~$ sudo apt-get remove achilles
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  achilles
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  achilles
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 160kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing achilles (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)
meleeglow@meleeglow-desktop:~$ Errors were encountered while processing:
 achilles




still stuck I think he meant the dpgk but who know I certainly don't

---

### Post by meng on 2007-01-02
Hmmm: what about
sudo apt-get install achilles

---

### Post by meleeglow on 2007-01-02
ok that worked thanks sry I doubted your compitance

---

