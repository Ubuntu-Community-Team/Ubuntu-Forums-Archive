---
title: "Startup: Is it Safe to Delete Scripts from  /etc/init.d?"
date: 2007-07-05
forum: General Help
---

### Post by OzzyFrank on 2007-07-05
Hi. I'm just trying to get my head around the boot process, and am wondering if one can delete scripts from /etc/init.d without haing any adverse effect. For example, Firestarter starts while Ubuntu is loading, but not like it actually does anything, as I have to maunally start it when I go online. So can I just delete its script to stop it loading at boot? Are there any negative repercussions? If it really is as simple as that, it would make a good troubleshooting tool for sussing out startup problems that look like they are being caused by an app. And yeah, a nice and easy way to prevent apps (that make themselves part of the boot process) from loading.

---

### Post by scxtt on 2007-07-05
firestarter sets up the iptables rules at boot (run **sudo iptables -L** to see them), you're just starting the GUI front-end / editor ... i wouldn't delete things out of /etc/init.d, just the symbolic links in the runlevel you use [**who -r** to see, 2 by default] ...

---

### Post by Bothered on 2007-07-05
Firestarter (by default) runs with or without the GUI running. The startup script launches firestarter.

---

### Post by OzzyFrank on 2007-07-05
Thanks for the Firestarter info. I have no problems with it running at startup, but was using that as an example of deleting scripts (though thanks to your input I won't be touching the Firestarter script). And so far the consensus is not to touch scripts in that folder. Sorry, don't understand the "symbolic links in the runlevel" bit, so if anyone can explain what that means and entails, that would be great. Like I said, would mostly like to have control over what starts for troubleshooting, though occasionally I might prevent something from starting (though not Firstarter, hehe).

---

### Post by scxtt on 2007-07-05
a symbolic link is like a windows shortcut ... when a request is made for a file which is a symbolic link, the request is just passed on to the ACTUAL file ...

they show up like```
/etc/rc2.d/S99kdm --> ../init.d/kdm
```

the "brains" of starting up kdm are in /etc/init.d/kdm, but the symbolic link for run-level2 (the rc2.d directory) points to that ... so when you're booting up your box, it makes use of scripts in /etc/init.d w/o actually copying all of them repeatedly for each run-level ...

---

### Post by szf on 2007-07-05
I've heard that renaming rc scripts to all lower case will stop a startup run - while preserving the "default" system. Give that a try?
Start with:```
ls -l /etc/rc?.d
```

---

### Post by xarmian on 2007-07-05
From the README file located in /etc/rc?.d (where ? is any of the runlevel folders):

> The scripts in this directory are executed each time the system enters
this runlevel.

The scripts are all symbolic links whose targets are located in
/etc/init.d/ .

To disable a service in this runlevel, rename its script in this directory
so that the new name begins with a 'K' and a two-digit number, where the
number is the difference between the two-digit number following the 'S'
in its current name, and 100.  To re-enable the service, rename the script
back to its original name beginning with 'S'.

For a more information see /etc/init.d/README.


For example, I wanted to disable wifi-radar, so I renamed S20wifi-radar to K80wifi-radar

-Dave

---

