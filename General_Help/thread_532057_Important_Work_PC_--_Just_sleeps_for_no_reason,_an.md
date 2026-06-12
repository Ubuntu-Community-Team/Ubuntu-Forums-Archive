---
title: "Important Work PC -- Just sleeps for no reason, and never wakes"
date: 2007-08-22
forum: General Help
---

### Post by WinterWeaver on 2007-08-22
We have  4pc's with the same spec. 3 is running windows, and 1 is running ubuntu.

The Ubuntu Machine runs a zope and plone instance which we use locally, as well as a couple of other scripts to do specific updates across the network.

Note... none of these PC's every get's shut down, as they need to run constantly.

Here is the problem. The Ubuntu PC, will per random occasion just stop and go to sleep. Once it's sleeping, it wont wake again. We then have to switch off the power and start it again, and I'm sure it's causing damage to the disks? :(

At first I believed it may be because the Swap Space is full. But today, on a clean boot, it was running for about 5 mins, and then decided to tuck in for the afternoon. BAD PC! Wake up!!

Could someone please help me diagnose the problem, as we are loosing data from time to time because of this.

thanks,

WW

---

### Post by WinterWeaver on 2007-08-25
Assistance in diagnosis would be nice ^_^  (ie. bump)

---

### Post by WinterWeaver on 2007-08-27
Where do I start?

---

### Post by Austin_KW on 2007-08-27
Are you sure that it is going to sleep/suspending. Why not add a line with "exit" on the second line of /etc/acpi/sleep.sh

---

### Post by WinterWeaver on 2007-08-27
kkk... I'll give that a try... don't know how I'll go about testing it, because it happens randomly.

I believe that it's going to sleep, because for a split second, just before it all goes down, the screen get locked, ie. everything goes black, except for a dialog in the middle asking for the password to unlock the screen.... and then ... everything dies :P

Thanks, for the response, I'll try adding that in the script and see if anything improves. :)

EDIT: 2 Days -- No Random Sleeping, seems to be working

WW

---

