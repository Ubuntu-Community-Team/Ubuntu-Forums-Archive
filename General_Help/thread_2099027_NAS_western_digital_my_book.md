---
title: "NAS western digital my book"
date: 2012-12-28
forum: General Help
---

### Post by then_dude on 2012-12-28
Hello people,  

i have got a NAS my book from western digital.  it has an utp connection and usb. it holds a 500gb hardisk. 

I connected via utp. i finally got it's ip adress. 
but it asks for a password, i have already resetted the NAS, but typing in the default login and password (admin/admin) doesn't allow me to enter the setup of the machine...   

can anybody help me ?

 in nautilus i'm trying to connect to network and the i get
 "windows network" click on it
 "unable to mount location" , "failed to retrieve share list from server" 

thanks guys

---

### Post by irv on 2012-12-28
If you have the ip address, try pinging it. That would be a place to start.
Also you might have to call Western Digital support to find out what the default password is if you can't find it in the documentation that came with the hardware.

---

### Post by Mark Phelps on 2012-12-28
Don't have a Passport drive, but from what I read, the front-end to enter a password only works in Windows.

I also read that if you go into Windows and remove the password, then you should be able to get access in Linux to the drive contents.

As to contacting WD, good luck with that!  Don't be terribly surprised if they tell you they don't support Linux.

---

### Post by Habitual on 2012-12-28
I saved the contents of the Disc that came with my WD 3T "my Book Essential" and then formatted it prior to "using" it.

Never been asked for a password in any OS.
```
/dev/sdb1      fuseblk  2.8T   20G  2.8T   1% /run/media/jj/Keepers
```

---

### Post by then_dude on 2012-12-29
thanks guys,  i'll give it a try in windows. i'll keep you posted.   kind regards

---

### Post by then_dude on 2012-12-29
I logged on with windows and same as in linux, i did enter the logon and password, but i cannot enter the drive...  thanks

---

### Post by Habitual on 2012-12-30
I had to login via KDE and use one of the volume|disk|partition tools listed in the KDE Menu (It may have even been gparted...)
and NUKEd THE DRIVE'S existing {volume, partition} to ORBIT.

Then I created an HPFS/NTFS/exFAT partition.

This of course, wasn't necessary since I could access my drive's contents. (None of which was 'my stuff')

Have you considered opening a ticket at [http://support.wdc.com/](http://support.wdc.com/) ? 
Do NOT tell them about your inability to access the drive in Linux.
**Windows** is giving you the grief upon drive access. 

But you *should* [reset the device]("http://community.wdc.com/t5/My-Book-Live/admin-password/td-p/336563") first since that is where they will probably "go" in a support ticket. 

Don't mention Linux, you've never heard of it. What's Linux?

Here's a firmware upgrade link in case you want/need it.
[http://www.wdc.com/wdproducts/wdsmartwareupdate/firmware.asp?id=wdfMB30_Essential&os=WIN](http://www.wdc.com/wdproducts/wdsmartwareupdate/firmware.asp?id=wdfMB30_Essential&os=WIN)

Seems you should reset it.
I know I have done this to my My Book 1130 at least once. What model are you dealing with?

Subscribed with Interest...

---

