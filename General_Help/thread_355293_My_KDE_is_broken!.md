---
title: "My KDE is broken!"
date: 2007-02-07
forum: General Help
---

### Post by ubunutucyclotron on 2007-02-07
Help!

After a hibernate due to running out of battery my KDE is kaput. After logging in it just says failed to initialise sysint (if I recall) and then does nothing else. Good thing I had gnome installed just in case but I really want to get back to KDE.

Thing is KDE is reported as broken in adept and nothing I can do seems to fix it. I try re-install, uninstall another install all to no avail. Problem is now after uninstalling (although it still comes up as broken in adept) I now have no kontact and no email!!! This is officially a crises.

So what do I do? All I have is a kubuntu live cd which seems to have no repair option so I dont know if I can go ahead with it. I do have backups up everything in

/home/cyclotron/.kde/share/apps
/home/cyclotron/.kde/share/config
/etc

which I have done using simplebackup.

So is that enough for my email and other stuff to be working again if I do a fresh install from the live CD and then copy those directories back over? Can I do that or will I get permissions issues or something?


A bit in the dark here, thanks in advance...

---

### Post by etank on 2007-02-07
Try running ```
sudo aptitude -f install
```You may also want to look at some of the tutorials on [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php).

---

### Post by ubunutucyclotron on 2007-02-08
Hi.

Ok the result is something strange which I had noticed before. I run the command and double confirm that I want to go ahead, once that I want to remove kde and install kaddressbook, libcvsservice0 and liblcms1-dev and once to confirm that I want to install untrusted versions of these packages.

This is what goes on then:

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Err [http://kubuntu.org](http://kubuntu.org) dapper/main kaddressbook 4:3.5.5-0ubuntu1~dapper1
  404 Not Found
Err [http://kubuntu.org](http://kubuntu.org) dapper/main libcvsservice0 4:3.5.5-0ubuntu1~dapper1
  404 Not Found
Err [http://kubuntu.org](http://kubuntu.org) dapper/main liblcms1-dev 1.15-1
  404 Not Found
E: Unable to correct for unavailable packages

Whats with the 404s connecting to kubuntu.org? I am writing this post and surfing the net from the same machine so its internet connection is working. I have found that I can connect to za.archive.ubuntu.com and others so is something wrong with kubuntu.org?

Thanks.

---

