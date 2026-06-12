---
title: "Another E: Could not get lock /var/cache/apt/archives/lock... question."
date: 2017-11-08
forum: General Help
---

### Post by bobsone on 2017-11-08
Hi
As the title suggests I have a problem where **sudo apt dist-update **or** [B]sudo apt-get autoremove **[/B]returns:
[I]E: Could not get lock /var/cache/apt/archives/lock – open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/[/I]

The problem appears to be caused by tf-mscorefonts-installer_3.4 . I wanted some new fonts so had a look at installing a Msoft library but abandoned the idea when I saw I had to agree with a MS End User Licence Agreement (EULA). I abandoned the install by closing the terminal and am now stuck....  I have run **ps aux | grep apt** and received  the following;
```
root      4172  0.0  0.0  61864  4284 ?        S    10:00   0:00 sudo apt-get autoremove
root      4173  0.2  0.9 122416 77164 ?        S    10:00   0:00 apt-get autoremove
root      4198  0.0  0.7  88280 59300 pts/1    Ss+  10:01   0:00   /usr/bin/dpkg --status-fd 71 --unpack --auto-deconfigure   /var/cache/apt/archives/ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb
beartho+  4572  0.0  0.0  21292   988 pts/3    S+   10:06   0:00 grep --color=auto apt
```

I have tried removing the problem with **sudo rm /var/cache/apt/archives/lock **which didn’t help.  However running **sudo killall apt-get** did help to the extent that running **sudo apt-get autoremove **appears to complete successfully and returns:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ttf-mscorefonts-installer
The following packages will be upgraded:
  ttf-mscorefonts-installer
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0 B/29,5 kB of archives.
After this operation, 134 kB of additional disk space will be used.
Do you want to continue? [Y/n]
``` 

Unfortunately if I choose to continue "Y",  the terminal window is then completely taken over by  the very long MS EULA which I cant do anything with.  Closing the terminal returns the following warning: *There is still a process running in this terminal.  closing the terminal will kill it*     and when the terminal is closed I am back to where I started.

Any help appreciated
Regards.

---

### Post by howefield on 2017-11-08
Try typing n to abandon the install or select Y and use the tab key to select the appropriate yes/no or when the licence comes up, then press enter.

---

### Post by bobsone on 2017-11-08
Thanks for the reply.
Abandoning (typing n) doesn&#8217;t solve the problem, and subsequent **sudo apt-get autoremove   **and**   sudo apt dist-upgrade** return the two E: error lines.  Typing Y takes me to the MS EULA where all previous commands etc are gone and nothing works including enter.

But..
After I tried pressing enter on the EULA, I closed and reopened the terminal and retried **sudo apt-get autoremove**  this time I was informed I needed to first run **sudo dpkg --configure -a** (which I did).
I reran **autoremove **and got the same result.  I then tried removing the problem (**sudo rm /var/cache/apt/archives/lock**) followed by** autoremove **and it appears it is now working.
update, dist-upgrade and autoremove are working as before.

Does this mean the Msoft fonts are now gone - not installed?

---

### Post by howefield on 2017-11-08
Quick way to check if the fonts are gone would be to look at the fonts list in LibreOffice, the fonts are andale, arial, arial bold, comic, courier, georgia, impact, times new roman, trebuchet, verdana and webdings.

```
sudo apt purge ttf-mscorefonts-installer
```

should also ensure that the fonts are gone.

---

### Post by bobsone on 2017-11-08
Thanks for the help,
There are no MS fonts in writer ans ttf-mscorefonts-installer isn&#8217;t installed.
I should have trusted there would be a Times New Roman alternative (Liberation Serif) and spent a bit more time looking for it.... Would have saved me a lot of work.

Thanks again for your help,
Bob.

---

