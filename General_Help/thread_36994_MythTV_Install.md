---
title: "MythTV Install"
date: 2005-05-25
forum: General Help
---

### Post by malachakla on 2005-05-25
Hello,
Can anyone guide me through the install of MythTV?
I haven't found any really conclusive guide for the install.
Thanks very much!

---

### Post by Ramon on 2005-05-25
[http://www.mythtv.org/modules.php?name=MythInstall](http://www.mythtv.org/modules.php?name=MythInstall)

[http://www.cs.rit.edu/~css8044/?q=mythtv](http://www.cs.rit.edu/~css8044/?q=mythtv)

[http://www.google.com/search?hl=en&lr=&q=mythtv+howto+ubuntu&btnG=Search](http://www.google.com/search?hl=en&lr=&q=mythtv+howto+ubuntu&btnG=Search)

---

### Post by malachakla on 2005-05-27
I tried to install, but I get this error....
sudo apt-get install mythtv
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
mythtv: Depends: mythtv-frontend (= 0.18-1) but it is not going to be installe d
Depends: mythtv-backend (= 0.18-1) but it is not going to be installed
E: Broken packages

$ sudo apt-get install mythtv mythtv-frontend mythtv-backend
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
mythtv-backend: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is t o be installed
Depends: libmyth-0.18 but it is not going to be installed
Depends: libqt3c102-mt (>= 3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed
mythtv-frontend: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
Depends: libmyth-0.18 but it is not going to be installed
Depends: libqt3c102-mt (>= 3:3.3.4) but 3:3.3.3-7ubuntu3 is t o be installed
E: Broken packages

Thanks!

---

### Post by WhisQuila on 2005-06-13
I tried to install via Synaptic and can't get it to work.

I really like Ubuntu and really suck at linux, so i want MythTv to work with Ubuntu but i havn't figured out how to do it.

---

### Post by chaumurky on 2005-06-13
I think, for the moment you will have to install version 0.17. If you **apt-cache search mythtv** you will see that this version is available and so are all the plugins for it.

EDIT: Hmm, it looks like 0.18 has been pulled anyway - perhaps for the above reason.

---

