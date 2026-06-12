---
title: "Power shut of during Google Chrome Update..."
date: 2013-05-26
forum: General Help
---

### Post by entikryst on 2013-05-26
...via update manager.

Relaunched update manager through terminal
-Brings up error window that states Package Operation Failed. The installation or removal of a software package failed.
-Clicking Try Again brings up the same window.
-Clicking OK brings up this error window [http://i.imgur.com/7R1Nzgz.png]("http://i.imgur.com/7R1Nzgz.png")
-Clicking Continue brings up a suggestion to run (sudo apt-get install -f)
-Running this command brings up the error E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
-Running (sudo dpkg --configure -a) brings up dpkg: error: parsing file '/var/lib/dpkg/updates/0006' near line 0:
 newline in field name `to'
-So back to this error window [http://i.imgur.com/7R1Nzgz.png]("http://i.imgur.com/7R1Nzgz.png")
-Clicking Partial Upgrade also bring up-I've tr the suggestion of running (sudo dpkg --configure -a)
  which also did not get me anywhere.
-I tried (sudo apt-get remove google-chrome-stable) with the same results
-I've tried (sudo apt-get install google-chrome-stable) with the same results
I haven't had any updates for any apps or the OS in about a week because of this.
I really don't want to reinstall Ubuntu or remove my profile from chrome. 
What do I do???

---

### Post by hansdown on 2013-05-26
Hi  entikryst.

!0.04 reached end of life on may 9th.

No more updates are forthcoming.

---

### Post by tgalati4 on 2013-05-26
Try:

```
sudo apt-get clean
sudo apt-get check
```

---

### Post by entikryst on 2013-05-26
same error
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by tgalati4 on 2013-05-27
```
cat /var/lib/dpkg/status
grep Chrome  /var/lib/dpkg/status
sudo dpkg -P -a
```

The first command dumps out the contents of the dpkg status file, for all packages installed on your system.  The second command filters that down to "Chrome".  Use chrome or Google or google to find the package.  If the status is "pending", then that means it is partially installed.  The third command purges (removes and deletes configuration files) any packages in "pending" status (-a switch).  If the Chrome package is other than "pending", please cut and paste it's status into this thread.

The --configure switch will attempt to complete the installation of any pending packages (-a switch), but if your package download got interrupted, then that won't work correctly.  So you need to delete and purge (remove all files of the offending package) and download again and reinstall.  Avoid power interruptions.

---

### Post by entikryst on 2013-05-27
dpkg: error: parsing file '/var/lib/dpkg/updates/0006' near line 0:
 newline in field name `to'

---

### Post by tgalati4 on 2013-05-27
tgalati4@Mint14-Extensa ~ $ ls -la /var/lib/dpkg/updates
total 8
drwxr-xr-x 2 root root 4096 May 24 18:09 .
drwxr-xr-x 8 root root 4096 May 24 18:09 ..

Although I don't like to do this, manually delete anything in /var/lib/dpkg/updates.

It appears that you have some partial updates that need to deleted manually, because dpkg doesn't know how to handle them.

---

### Post by entikryst on 2013-05-28
You are the best tgalai4!  Everything works just fine.  I ran the command sudo rm 0000 0001 0002 0003 0004 0005 0006 0007 0008 0009 (probably and easier way to do it but I got it done)

---

