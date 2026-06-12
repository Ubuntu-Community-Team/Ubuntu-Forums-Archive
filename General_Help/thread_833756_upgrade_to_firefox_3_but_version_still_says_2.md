---
title: "upgrade to firefox 3 but version still says 2"
date: 2008-06-18
forum: General Help
---

### Post by jqgatsby on 2008-06-18
I upgraded to firefox 3 today (as prompted by my ubuntu update manager), but when I look at Help -> "About Mozilla Firefox" it still says version 2.x.  I've tried going to /usr/lib/firefox-3.0 and typing firefox directly from the command line, but it still says version 2!

Any help would be appreciated, as I am keen to reap the benefits of version 3!

-John

---

### Post by z0mbie on 2008-06-18
You probably have both Firefox 2.0 and 3.0 installed. You can uninstall Firefox 2 by typing:

```
sudo aptitude remove firefox 
```

For future reference Firefox 3 in the repository is known as **firefox-3.0**

---

### Post by jqgatsby on 2008-06-19
Unfortunately, that did not work. The version of firefox is still 2.x.  Other ideas would be greatly appreciated!

---

### Post by nicknormal on 2008-06-19
agreed. that didn't work for me either!

I'm on Ubuntu 8.04. done all the tricks. deleted profiles, reinstalled, used aptitude, synaptic package manager, downloaded the .tar.bz2 and installed from terminal... nothing works!

---

### Post by kool_kat_os on 2008-06-19
did you look in synaptic and see what was installed?

---

### Post by DrMilo on 2008-06-19
I found this:

"If you try installing it on Dapper, then it fails to find the install files when it tries to FTP it, because its looking for firefox-3.0.tar.gz and the file is actually firefox-3.0.tar.bz2.
I edited the ubuntuzilla script to change the tar.gz to tar.bz2 in the 2 places necessary, and the install worked. However, firefox wouldn't run because v3.0 needs gtk-2.10 and dapper comes with gtk 2.8 - and their appears to be no 2.10 available for dapper."

[http://tinyurl.com/6mg7ru](http://tinyurl.com/6mg7ru)

Can anyone speak to this? I can't upgrade either.

---

### Post by aysiu on 2008-06-19
If you're using Hardy, the command should be ```
sudo apt-get update && sudo apt-get install firefox firefox-3.0 && sudo apt-get remove firefox-2
``` If you're using Gutsy, try [this](http://www.psychocats.net/ubuntu/firefox#terminal).

---

### Post by jqgatsby on 2008-06-19
I've found that typing in 'firefox-3.0' from the command line correctly launches firefox-3.0 UNLESS I already have an instance of firefox 2.x running (in which case another instance of 2.x launches).

However if I type "firefox", it still launches the old firefox-2.x

This is odd, because according to synaptic package manager I don't even have 2.x installed on my system anymore.

A reasonable workaround is to just update my panel links to run 'firefox-3.0' and not 'firefox'.

Further investigations:
If I type "which firefox", I get /usr/bin/firefox which in turn points to /opt/firefox/firefox

when I run '/opt/firefox/firefox' I get the latest firefox iff i already have an instance of firefox-3.0 running.  If not, I get firefox-2.x.  Hypothesis: Synaptic package manager is not properly removing firefox-2.x from the system, and somehow that breaks an assumption in the startup script.  Could someone verify this, and perhaps indicate where to file a bug?

---

### Post by aysiu on 2008-06-19
Clearly you installed the Mozilla build of Firefox 2 previously. So we can fix that: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
```

---

### Post by jqgatsby on 2008-06-19
I tried uninstalling firefox-2 manually (with firefox closed), but I get the following errors:

>> sudo apt-get remove firefox-2
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

So apparently the system is having trouble uninstalling firefox-2.  I conjecture that if we were able to completely remove firefox-2, this problem would go away.

At this point I have a workaround (as mentioned above), so I'm going to move on.

---

### Post by jqgatsby on 2008-06-19
Clearly to you, aysiu :)
I wonder why I did that.
Your commands worked, now i can run firefox from the command line and all is well.

---

### Post by aysiu on 2008-06-19
> **jqgatsby said:**
> ```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
``` This error appears when you have more than one application trying to access package management at the same time.

The applications that have access to package management are:
Synaptic Package Manager
Add/Remove
Update Manager
gDebi
dpkg
apt-get
aptitude

If you have more than one of those open, close them, and keep only one active at a time.

---

### Post by mempman on 2008-06-19
> **jqgatsby said:**
> I tried uninstalling firefox-2 manually (with firefox closed), but I get the following errors:

>> sudo apt-get remove firefox-2
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

So apparently the system is having trouble uninstalling firefox-2.  I conjecture that if we were able to completely remove firefox-2, this problem would go away.

At this point I have a workaround (as mentioned above), so I'm going to move on.

If u are getting this error on the command line, then its prolly cause you have Synaptics Package Manager open as well, try closing it and retry.

---

