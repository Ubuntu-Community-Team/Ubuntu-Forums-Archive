---
title: "Update Manager - Segmentation Fault"
date: 2008-05-22
forum: General Help
---

### Post by jmszr on 2008-05-22
When I click System > Administration > Update Manager it comes up (grayed out) and the small "Starting Update Manager" window comes up but when the bar is half filled it disappears. I searched the forums and to make it short this is the result: jeff@jeff-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Segmentation faulty tree... 50%
jeff@jeff-desktop:~$ sudo apt-get install --reinstall update-manager update-manager-core
Reading package lists... Done
Segmentation faulty tree... 50%
jeff@jeff-desktop:~$ sudo apt-get remove --purge update-manager update-manager-core
Reading package lists... Done
Segmentation faulty tree... 50%
jeff@jeff-desktop:~$ sudo apt-get install update-manager update-manager-core
Reading package lists... Done
Segmentation faulty tree... 50%
Synaptic and Add/Remove Applications also do not stay up.
The last update I did was 5/21 p.m. 2 security updates that I doubt had anything to do with this problem but I certainly don't know.
Any help that anyone could give me would be appreciated.
Thank you.
jmszr                     Ubuntu 8.04

---

### Post by N.N. on 2008-05-22
According to a forum thread from the archive, [http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563), you should be able to fix the problem by issuing the following command from a terminal: ```
sudo rm /var/cache/apt/*.bin
```

---

### Post by jmszr on 2008-05-22
N.N.,
    That did the trick.
                        Thank you,
                                  jmszr

---

### Post by SneakyWho_am_i on 2008-05-25
N.N.,
You are my hero.

---

### Post by geertv on 2009-08-19
The fix still works :-) 
Thanks !

---

### Post by tijmz on 2009-09-07
Thanks for this suggestion - it works for me, too.

However, I encountered this error twice and wondered if there's anything I could do to prevent it from showing up again :)

---

### Post by Ridgefield on 2010-02-01
I have the same issue as tijmz, however I am constantly using

```
sudo rm /var/cache/apt/*.bin
```
Is there a way to fix this problem permanently. I run into to it daily. . .

---

### Post by Ridgefield on 2010-02-04
Error fixed. . . Seemed I had some faulty ram, replaced it now all is good.

---

### Post by juliobahar on 2010-04-06
Thanks for the fix guys Update-manager seems to work fine now. Great Job.

---

### Post by camdude on 2010-05-15
Thanks! That works great - I've had this problem all the way from Ubuntu 8.10, all the way until 10.04... I just had to work with the applications that were on the computer before the problem (which can get really annoying, especially if you need to have an application for work) Thanks Again! :KS

---

### Post by Carlos Limited on 2010-06-30
I Have the same problem and i typed the code on the terminal. And yes i was able to open the update manager. However when it is now trying to update i received this error code:

'E:Problem parsing dependency Depends, E:Error occurred while processing horae (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_lucid_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Basically, i dont understand what is happening now on the Update Manager.
Need Help Please... Anyone?

---

### Post by Carlos Limited on 2010-06-30
What the heck i was able to fix it.... gee... I just need to restart my computer... and there you go, it's running well now.

---

### Post by dekrit on 2010-07-13
Thanks N.N.
You saved my day

---

### Post by tauren on 2011-11-04
Sweet, this fix still works on 11.04. Just about to upgrade to 11.10.

---

### Post by oldos2er on 2011-11-05
Closed, please don't bump old threads.

---

