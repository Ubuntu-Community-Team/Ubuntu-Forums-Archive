---
title: "Update manager failed"
date: 2008-05-06
forum: General Help
---

### Post by SyCo123 on 2008-05-06
Update manager failed to some files. What can I do to update?
It did fetch about 30 and updated what it could.

Here's all the failed package right from the update manager window. This is 7.10 in virtual box.


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.81.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.81.2_all.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.81.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.81.2_i386.deb)
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb)
  404 Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb)
  404 Not Found

---

### Post by tamoneya on 2008-05-06
the repository has been a little slow today on some servers.  Try changing the server or waiting a couple hours and trying again.

---

### Post by SyCo123 on 2008-05-09
This is still broken. I've updated successfully on another machine, and I'm typing this from the one with the problem, so the network connection is OK.

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.81.2_all.deb
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.81.2_i386.deb
  404 Not Found [IP: 91.189.88.45 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb
  404 Not Found


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.13+1nobinonly-0ubuntu0.7.10_i386.deb
  404 Not Found



```

---

### Post by markharding557 on 2008-05-09
try some different servers since you can access the internet but not the repository servers it would suggest the problem is the servers

---

### Post by SyCo123 on 2008-05-19
This problem lingered and lingered so I tried on the command line

sudo apt-get update

and it connected to servers just fine. Then in the update manager there were lots of new updates listed. I clicked apply and the update went through OK this time.

It included an update to the update manager so if this was a bug I'll bet it's already fixed :)

Thanks for the suggestions.

---

### Post by Don_Dragon on 2008-05-22
I'm having a similar problem myself.  Can't update or install anything using the GUI, but using the terminal works fine.  When I try the update manager, asking it to install or even check for updates, it just hangs...

---

### Post by Don_Dragon on 2008-05-23
This solved the problem.  Turns out, while trying to enable networking, I messed up the host name, which broke the manager's ability to check for my password.

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

