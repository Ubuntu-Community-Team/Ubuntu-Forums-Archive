---
title: "HP 4050 Only printing from tray 4"
date: 2007-10-02
forum: General Help
---

### Post by ashkev on 2007-10-02
I am running Edubuntu on a server with 10 thin clients, as well as my HP Pavillion ZV5000 laptop.  Until recently printing was working fine from both machines to our HP4050.  We have HP4050 at two locations and printing was working fine to both of them.  

As of an update about a week ago, (maybe more) most jobs are printing to tray 4 (a manual feed tray) rather than the default tray 3.  When I try to open hp-toolbox I get this error:

```
kevin@kevin-laptop:~$ hp-toolbox
error: PyQt not installed. GUI not available. Exiting.
error: PyQt/Qt initialization error. Please check install of PyQt/Qt and try again.
```

Any help with this would be appreciated.

---

### Post by ashkev on 2007-10-02
Update:

I found this [bug]("http://https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/86893") and after doing: 
```
$ sudo apt-get install python-qt3
```
I was able to open hp-toolbox, but even after reinstalling the hp 4050 through the hp-toolbox, I am unable to make it print from anything but the tray 4.  If I print from Open Office, it works fine, but Firefox or the test page only print to tray 4....

---

