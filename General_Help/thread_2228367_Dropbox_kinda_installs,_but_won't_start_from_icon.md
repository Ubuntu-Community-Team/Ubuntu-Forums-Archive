---
title: "Dropbox kinda installs, but won't start from icon"
date: 2014-06-07
forum: General Help
---

### Post by RogerDavis on 2014-06-07
I can install Dropbox either from the Software Center or directly, but once installed it won't start to let me pick files, etc.

When I click the icon, nothing at all happens.

How can I fix this?

---

### Post by bapoumba on 2014-06-07
Are you still on Precise ?
Do you have the nautilis-dropbox package installed ?
Can you start it with ```
dropbox start
``` ?

---

### Post by RogerDavis on 2014-06-07
Are you still on Precise ?  - Yes.
Do you have the nautilis-dropbox package installed ?  -  I tried this with both the nautilus and direct-from-dropbox packages.
Can you start it with Code: dropbox start  -  No, no result from this at all.

I suspect that one of the recent updates started the problem, it worked when I first installed it from the Software Center.

---

### Post by bapoumba on 2014-06-08
OK, first to see what you have installed :

```
bapoumba@SonyBlue:~$ dpkg -l *dropbox
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  dropbox        <none>       <none>       (no description available)
ii  nautilus-dropb 1.6.1-1      i386         Dropbox integration for Nautilus

bapoumba@SonyBlue:~$ apt-cache policy dropbox
dropbox:
  Installed: (none)
  Candidate: (none)
  Version table:

bapoumba@SonyBlue:~$ apt-cache policy nautilus-dropbox
nautilus-dropbox:
  Installed: 1.6.1-1
  Candidate: 1.6.1-1
  Version table:
 *** 1.6.1-1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/multiverse i386 Packages
        100 /var/lib/dpkg/status

```

The idea would be to remove anything you have installed and start over. If you installed from the Software Center, nautilus-dropbox should be here.

Once you do not have anything left (you can use sudo apt-get purge <package> if it was installed with the Software Center/apt-get/Synaptic), you can install it again from the command line so that we can see any error messages and work from them :
```
sudo apt-get update
sudo apt-get install nautilus-dropbox
```

Please post the outputs to the first 3 commands and any error message you get upon updating or installing nautilus-dropbox.

---

