---
title: "Likewise on Gutsy?"
date: 2008-04-15
forum: General Help
---

### Post by seeker1458 on 2008-04-15
I am trying to get the LikeWise-open version to install on my gutsy box. I can't find it in the repos? Is it only available for Hardy? I have downloaded the "LikewiseOpen-4.1.0.2773-linux-i386-deb-installer" but can't get it to install? It isn't a .deb file, the filename is exaclty as typed. Any help available?

---

### Post by cdenley on 2008-04-15
Yes, it looks like that package is [only available for hardy]("http://packages.ubuntu.com/search?keywords=likewise-open&searchon=names&exact=1&suite=all&section=all").

Maybe that file needs to be executed
```

chmod 755 LikewiseOpen-4.1.0.2773-linux-i386-deb-installer
sudo ./LikewiseOpen-4.1.0.2773-linux-i386-deb-installer

```

---

### Post by fguilhon on 2008-04-15
If it's not a deb, maybe it is binary executable. Try ```
chmod +x LikewiseOpen-4.1.0.2773-linux-i386-deb-installer
```
and then (on the same directory) ```
./LikewiseOpen-4.1.0.2773-linux-i386-deb-installer
```
But beware that it is a executable and may damage your system.

---

### Post by seeker1458 on 2008-04-15
Awesome thanks cdenley  After that just used the same procedure to run the GUI, and it says all is well.  Need to test some things, but looks like it worked.  Thanks alot.

---

### Post by paultwibill on 2008-04-24
Hi, 
I was having the same problems, will try your solution. 
I notice a couple of things 
1. Likewise does not appear to be in repos as promised elsewhere!
2. It is promised to be part of next Ubuntu release
3. The Likewise-open packages appear to be Bitrock InstallBuilder packages, not come across this before! requires superuser access but gives no option to enter password.  As far as I can tell I am logged on as a superuser!! not sure what else to do to become superuser & run the package!

Just tried your options package starts to run as before but still asks for superuser credentials & no option to enter a password.
Tried using Sudo...but find this confusing I'm never entirely sure where in the file structure I'am when using sudo. It reports "command not found". I guess the package and the sudo user location must be one & the same. Not sure how to either move sudo to where the package is or move package to sudo location.

---

### Post by Chad.S on 2008-04-24
> **seeker1458 said:**
> Awesome thanks cdenley  After that just used the same procedure to run the GUI, and it says all is well.  Need to test some things, but looks like it worked.  Thanks alot.

I've had it installed on Gutsy for quite some time now. Just some quick advice...

I had to modify my /etc/init.d/rc.local file and add the following line at the end...

/etc/init.d/likewise-open start

Otherwise the winbind service doesn't start before the login. Also, I noticed some stranger behavior when opening up a terminal after logging in as a domain user. When starting the terminal it was scanning for a groupid and eventually stopped with an error but would let me use the terminal anyway. Upon looking at it further a group name that likewise creates has an invalid character (winbindd_priv). I'm unsure if this is related to the issue I get at the terminal or not, but I would suspect it may be.

I'm looking forward to starting with a fresh install of Gutsy and testing out likewise again.

---

