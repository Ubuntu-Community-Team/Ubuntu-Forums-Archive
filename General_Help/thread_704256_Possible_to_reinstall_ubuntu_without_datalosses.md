---
title: "Possible to reinstall ubuntu without datalosses?"
date: 2008-02-22
forum: General Help
---

### Post by Dojan5 on 2008-02-22
Okay.
I messed things up in my Ubuntu Installation.
Noone seem to have the solution to my current problem and my Mp3 players magically dont work on Ubuntu anymore.
So well. I want to reinstall Ubuntu.
Look more like it as a repair install.
Heres what i want to do.

I want to reinstall Ubuntu core stuff like start up and so on, BUT, i dont want to lose my User Profiles and those files and so on.

The problem is that i have Ubuntu installed on one partition and my home directories on another partition. I want to keep it that way, but i want ubuntu to keep my user profiles and such stuff.
How do i make it that way that it KNOW that the Home directory is on another partition and that it USE that directory?
I cant back up stuff on the computer since my CD burner have crashed.
Please help.
Thanks
/
Joel

<<<EDIT>>>
Last time it automatically knew  that the partition was a home directory, but, this time?:lolflag:
Thanks for baring with me :)

---

### Post by forestpixie on 2008-02-22
use the manual option when you get to the partitioner

create the / mount point for the install against the original / partition and click the format box

create the /home mount point against the original /home partition - but don't let it format - then all should be ok 

but without backups - if something does go wrong you'd likely lose stuff you don't want

if there's stuff you really can't lose is it too much for a usb stick, or maybe use one of those online storage places through the livecd

---

### Post by kesman on 2008-02-22
In the ubuntu installer you can select what partition to mount where. Just select your existing /home -partition to be mounted as your new /home and remember NOT to format the partition.

---

### Post by Dojan5 on 2008-02-22
> **forestpixie said:**
> use the manual option when you get to the partitioner

create the / mount point for the install against the original / partition and click the format box

create the /home mount point against the original /home partition - but don't let it format - then all should be ok 

but without backups - if something does go wrong you'd likely lose stuff you don't want

if there's stuff you really can't lose is it too much for a usb stick, or maybe use one of those online storage places through the livecd

Thanksthankthanks!
You gave me the best idea ever.
I can store the stuff on my Windows Partition!
And thanks for explaining, i printed it out.
And currently im stuck with the Live CD so...
Anywho thanks!!!!!!!!

---

### Post by seventhc on 2008-02-22
I think if you don't change partition sizes, keep the same mount points your */home* directory will be safe.
But wait for a second or third opinion on this first.
You say you can't back up to cd but you might be able to make an archive and email it to yourself.
Not sure what your size limit is, but there are places that will host files for you if email isn't an option.
Because a backup is preferable, since even if you do everything correctly, there is always a chance it will fail. And then everything would be gone.

---

### Post by seventhc on 2008-02-22
> online storage places through the livecd
They have that on the live cd??
is it mediamax or mediafile??
I never saw that on ther cd, havent really looked though.
Can you please tell me where it is on the livecd??
Thanks.

---

### Post by forestpixie on 2008-02-22
no i meant get to one of those online storage web wotsits with firefox - when you've got the livecd going - shame there isn't one though on the cd - that would be good indeed :D
> 
I can store the stuff on my Windows Partition! - it turned out to be useful after all then!

can you make sure to mark thread when you're happy.

---

