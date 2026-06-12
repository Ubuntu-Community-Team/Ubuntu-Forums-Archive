---
title: "Stuck with aborted install"
date: 2015-05-08
forum: General Help
---

### Post by Fuser77 on 2015-05-08
Good evening,

I was trying to install Apache Open Office using GDebi Package Installer.
Somehow the install got aborted and I can not get Ubuntu to restart the whole installation process.

I tried opening Synaptic but it sends an error message:

E: The package openoffice-debian-menus needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Synaptic does seem to be willing to start up until we solve this issue.

I tried some procedures to purge files but I don't know if I used the right ones; so far nothing worked.

Your help is much appreciated!

Thank you.

---

### Post by mörgæs on 2015-05-09
Please boot the computer, run ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` and post the results.

---

### Post by Fuser77 on 2015-05-10
Thanks for getting back to me!

It's done, how can I attach the screenshots?

---

### Post by mörgæs on 2015-05-10
Don't use root when working in Buntu:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Does this help?
```
 sudo apt-get remove --purge openoffice-debian-menus
```

Better to just copy and paste the text than taking screen shots.

---

### Post by Fuser77 on 2015-05-10
Hi Morgaes,

This is what it gives:

labo@alf-Latitude-D610:~$ sudo apt-get remove --purge openoffice-debian-menus
[sudo] password for labo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package openoffice-debian-menus needs to be reinstalled, but I can't find an archive for it.

:sad::sad::sad:

---

### Post by mörgæs on 2015-05-12
Sorry, I don't know where to go from here.

---

### Post by Fuser77 on 2015-05-12
Thank you, Morgaes!

Software Index Broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Anybody can help?

:confused:

---

### Post by sudodus on 2015-05-12
Maybe it helps with the following commands, particularly those to fix broken packages, and then repeat the other commands

```

# Oldfred's command list for cleaning and repairing
 
#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

#refresh
[COLOR=#0000cd]sudo apt-get update[/COLOR] #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
[COLOR=#0000cd]sudo apt-get dist-upgrade[/COLOR]

# fix Broken packages -f 
[COLOR=#0000cd]sudo apt-get -f install
sudo dpkg --configure -a[/COLOR]

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a 

# added zika's tip for problems with hash sum mismatch

sudo rm /var/lib/apt/lists/*
sudo apt-get update

```

---

### Post by Fuser77 on 2015-05-12
Thank you, Sudodus.

Most of these commands give me the same reply:

E: The package openoffice-debian-menus needs to be reinstalled, but I can't find an archive for it.

I am still unable to open Synaptic.
Is there anything else we can try?

Once again, thanks for your help!

---

### Post by QDR06VV9 on 2015-05-12
is libreoffice installed?
if so read this [URL="https://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=65586"]https://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=65586


[/URL]

---

### Post by Fuser77 on 2015-05-13
Thank you so much, Runrickus.
None of that have helped, but I'll re-post the issue in the Open Office forums.
Let's see what happens!

---

### Post by QDR06VV9 on 2015-05-13
Most Welcome:D
Hope you get it solved.
But I am really surprised that this
```
sudo apt-get remove libreoffice-common*
```
Followed by
```
sudo apt-get remove openoffice4
```
Did not work though:-k
Best of Luck

---

### Post by Fuser77 on 2015-05-13
Hi!

Just for your information, this issue has been solved with the help of the OpenOffice forums.

Thank you ALL so much for your support!!!

---

### Post by QDR06VV9 on 2015-05-13
Would you share what the fix was or at least a link to it.
It helps others while looking for the same.;)
Regards
Never mind found it [https://forum.openoffice.org/en/forum/viewtopic.php?f=16&p=352173#p352173](https://forum.openoffice.org/en/forum/viewtopic.php?f=16&p=352173#p352173)
Glad you got it sorted.

---

