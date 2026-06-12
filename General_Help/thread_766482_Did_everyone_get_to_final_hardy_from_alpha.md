---
title: "Did everyone get to final hardy from alpha?"
date: 2008-04-25
forum: General Help
---

### Post by rajeev1204 on 2008-04-25
hi all

I have been using hardy since alpha 6 ,but now it seems i havent got any updates and grub entry still shows development version.

Update manager seems to hang in between .

---

### Post by kpkeerthi on 2008-04-25
The servers could be flooded at the moment (& probably for a week). Switch to a mirror closest to you under System -> Admin -> Software Sources and try again from command line.
```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by bilal.17 on 2008-04-25
if you have been updating whenever there is an update through update manager then you are already using hardy, i did that too and my grub entry still says development as well, i believe you can change that by editing the grub file which at the moment i cant recall where it is

---

### Post by bilal.17 on 2008-04-25
ok i found it 
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by rajeev1204 on 2008-04-25
hmm ok

But i remember last time when using feisty  and upgrading from beta to final, it did remove that development entry from grub.

I guess ill do that manually .Iam probably on final .Update manager seems to fail at some translation updates, then goes on further without issues.

thanks anyways,

rajeev

---

### Post by dubrict on 2008-04-25
No matter what server I fetch updates from, it tells me there are no updates.  It seems strange that it's been like this for 2 days now.  Did the repositories change when the final version of hardy was released??

---

### Post by ibuclaw on 2008-04-25
I believe the ISOs were finialised two days ago.
And they've been preparing for a World-Wide shipping and uploading to servers for all of us to download.

And besides, it only seems righteous that the devs are taking a well deserved celebration/break.

The updates should start pouring through again in about 3-5 days. If not a week.

Regards
Iain

---

