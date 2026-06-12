---
title: "Shutdown while Synaptic was running,"
date: 2008-01-29
forum: General Help
---

### Post by Omnigoddess on 2008-01-29
I was trying to get wine to work so that I could access yahoo music via IE.

I tried one method, I can't remember what it was but I couldn't run the IE install, so I looked for a fix.

I went to their website and ran
"sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list"

Then went to Synaptic Package Manager and started to install.  I locked my computer while I went to do something.  I came back and couldn't get back in (I've had this problem previously), so I had to reboot.  Now synaptic gives me the error:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Opening Terminal and running "dpkg --configure -a" gets me the error:
"dpkg: requested operation requires superuser privilege"

I am the Superuser!  :cry:

I also can't get Matlab R2007a to install, but I think fixing the first problem might help.

Thanks to anyone who can help.  
Actually, thanks for just looking to see if you could.

---

### Post by louieb on 2008-01-29
Try 
```
sudo dpkg --configure -a
```
sudo is how your run stuff as the super user.

---

### Post by Lean 946 on 2008-01-30
try:
```
$ sudo su
```
will print:
```
Password:
```
type password.
and you got a root terminal
then:
```
dpkg --configure -a
```
and i think its done

Lean!

---

### Post by Omnigoddess on 2008-01-30
Thanks to you both!  I'll try these when I get off of work.

---

