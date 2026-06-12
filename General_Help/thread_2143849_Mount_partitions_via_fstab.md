---
title: "Mount partitions via fstab?"
date: 2013-05-10
forum: General Help
---

### Post by GreatBunzinni on 2013-05-10
I have a Ubuntu 12.10 install, and I've noticed that it mounts a partition at startup which is listed on /etc/mtab and has no entry in /etc/fstab.  After a bit of digging, I've noticed that System Settings has an entry which sets this partition as "Automount on Login", but it appears there is no way to set the default permissions.

Does anyone know how to add this partition to fstab without causing any unforeseeable problems?

---

### Post by prodigy_ on 2013-05-10
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Morbius1 on 2013-05-10
> After a bit of digging, I've noticed that System Settings has an entry which sets this partition as "Automount on Login"
Where is that exactly - give the whole path to wherever this is in "System Settings".

---

### Post by GreatBunzinni on 2013-05-16
> **Morbius1 said:**
> Where is that exactly - give the whole path to wherever this is in "System Settings".

Sorry for the delay.  This last week has been a bit hectic.

The "System Settings" path is: "System settings" -> "Removable devices".


Update: I've just noticed that unsetting the option to mount a partition ends up having no effect on how Ubuntu automatically mounts partitions.

---

### Post by GreatBunzinni on 2013-05-16
> **prodigy_ said:**
> [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Thanks for the links.  Nevertheless, my main concern isn't about how to set fstab, but about what steps should be taken to avoid any possible clash between how those partitions are currently being mounted and adding them to fstab.  In other words, how to add this partition to fstab without causing any unforeseeable problems.  Simply adding entries to fstab sounds a bit too risky.

---

### Post by Morbius1 on 2013-05-16
> The "System Settings" path is: "System settings" -> "Removable devices".

There is no such path in Ubuntu at least not Ubuntu 12.10. Are you using Kubuntu?

I don't use KDE so I personally have no idea what if any interaction there is between "removeable  drives" and fstab. My guess would be none but that's clearly a guess.

Isn't there a Kubuntu subforum section here that you could post this question?

---

### Post by GreatBunzinni on 2013-05-16
> **Morbius1 said:**
> There is no such path in Ubuntu at least not Ubuntu 12.10. Are you using Kubuntu?

I believe it's Ubuntu with the KDE desktop installed afterwards.  


> **Morbius1 said:**
> 
I don't use KDE so I personally have no idea what if any interaction there is between "removeable  drives" and fstab. My guess would be none but that's clearly a guess.

Isn't there a Kubuntu subforum section here that you could post this question?
The desktop environment for me is a non-issue.  If it isn't possible to configure how Ubuntu automatically mounts drives without running Unity then I can always fire up Unity specifically for this purpose.

---

### Post by Morbius1 on 2013-05-16
>  If it isn't possible to configure how Ubuntu automatically mounts  drives without running Unity then I can always fire up Unity  specifically for this purpose.         

There is very much a way to configure how Ubuntu / Lubuntu / Xubuntu and I would guess how the majority of other DE's automatically mounts a partition at boot and it requires you to edit fstab.

The specific question here however is an interesting feature of KDE that allows the user to apparently go to a utility and select to have ceratin partitions that are not part of the base install mount at the user's login not at boot. The phrase you used was: " I've noticed that System Settings has an entry which sets this partition as "Automount on Login". 

I personally am not a KDE user so I have no idea what that's doing and if it conflicts with in any way the fstab method which is why I suggested posting your question in the KDE or Kubuntu part of this form if we have one.

---

### Post by GreatBunzinni on 2013-05-17
> **Morbius1 said:**
> There is very much a way to configure how Ubuntu / Lubuntu / Xubuntu and I would guess how the majority of other DE's automatically mounts a partition at boot and it requires you to edit fstab.


You've misread the question.  It wasn't about whether it was possible to use fstab to mount a partition.  The question, which was presented from the start of this thread, was how to add this partition to fstab without causing any unforeseeable problems, as Ubuntu was already mounting the same partition through a different method.


> **Morbius1 said:**
> 
The specific question here however is an interesting feature of KDE that allows the user to apparently go to a utility and select to have ceratin partitions that are not part of the base install mount at the user's login not at boot. The phrase you used was: " I've noticed that System Settings has an entry which sets this partition as "Automount on Login". 

I personally am not a KDE user so I have no idea what that's doing and if it conflicts with in any way the fstab method which is why I suggested posting your question in the KDE or Kubuntu part of this form if we have one.

I've installed KDE only after this particular computer was already mounting that partition automatically.  At that time, this computer was running Ubuntu with Unity as its default desktop environment.  In other words, Ubuntu was already configured to automatically mount that partition without KDE being in the picture. KDE has nothing to do with this.

In addition, that setting appears to have no effect or influence on how Ubuntu automatically mounts a drive.  Even when I disable that option, the drive keeps on being mounted automatically.

---

### Post by GreatBunzinni on 2013-05-17
In the event this information is useful to anyone, here's the mtab entry for the partition which is being automatically mounted.

```

/dev/sdb1 /media/DATA fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

```

Update: it's a NTFS partition.

---

### Post by Morbius1 on 2013-05-17
If I take KDE out of this situation:

[1] There is no "Automount at Login" under System Setting or anywhere else I can find.
[2] Ubuntu doesn't automount anything unless it's in fstab, you created a script to do the mounting, or it's an external storage device.

It may appear to the user to be auto mounted since there is a link to the unmounted partition under Devices in Nautilus but it's only mounted when selected. The biggest clue to this being the case is that permissions to access the ntfs partition is limited to you alone.

And except for the mount point it would mount it just like you posted:
> /dev/sdb1 /media/DATA fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
There's only one teensie little problem: it's mounting it in the wrong place.
Prior to Ubuntu 12.10 the system would mount these partition to /media/LABEL just as you posted but from Ubuntu 12.10 on it mounts to /media/$USER/LABEL so your line should look like this:
> /dev/sdb1 /media/your-user-name/DATA fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
Curiouser and curiouser.

Sure you don't already have an entry for this in /etc/fstab? By any chance is this a Wubi install?

---

### Post by GreatBunzinni on 2013-05-21
> **Morbius1 said:**
> 
[2] Ubuntu doesn't automount anything unless it's in fstab, you created a script to do the mounting, or it's an external storage device.


This doesn't appear to be true.  My /etc/fstab only mounts two partitions: / and swap.  No windows partition is mentioned in /etc/fstab

Meanwhile, two different windows partitions are listed on /etc/mtab, and both are mounted automatically.

> **Morbius1 said:**
> 
It may appear to the user to be auto mounted since there is a link to the unmounted partition under Devices in Nautilus but it's only mounted when selected.


This isn't the case.  All windows partitions are mounted without even running any file manager.  As I'm using KDE, and the default file manager is Dolphin, Nautilus isn't being used or clicked on.

In addition, KDE includes the Device Notifier widget, which lists which drives have been mounted and offers options to unmount them as well.  This widget does not list any windows partition.

> **Morbius1 said:**
> 
Sure you don't already have an entry for this in /etc/fstab? By any chance is this a Wubi install?
I'm sure these partitions aren't mounted through /etc/fstab.  I'm not aware which method was used to install Ubuntu on this computer.

---

### Post by GreatBunzinni on 2013-05-21
> **GreatBunzinni said:**
> 
Meanwhile, two different windows partitions are listed on /etc/mtab, and both are mounted automatically.

To be more precise, only one partition is actually a windows partition.  The other is a separate hard drive which happens to be formatted with a NTFS file system.

---

### Post by prodigy_ on 2013-05-21
> **GreatBunzinni said:**
> My /etc/fstab only mounts two partitions: / and swap.  No windows partition is mentioned in /etc/fstab
Meanwhile, two different windows partitions are listed on /etc/mtab, and both are mounted automatically.

I'm not familiar with KDE (nor do I want to touch it with a 10-foot computing pole) but fstab should always take precedence. Simply try adding records for partitions you want to mount and see if it works. If you're concerned about data integrity, I don't think that an attempt to mount an already mounted partition could case any damage to data. I've never heard of such occurrences either. Still, nothing stops you from making a backup first, especially since it's handy to have one in any case.

---

### Post by Morbius1 on 2013-05-21
First and Foremost I would follow the sage advice of [COLOR=#0000cd]**prodigy_**[/COLOR] because this doesn't seem possible:
> My /etc/fstab only mounts two  partitions: / and swap.  No windows partition is mentioned in /etc/fstab
Meanwhile, two different windows partitions are listed on /etc/mtab, and both are mounted automatically.

Unless ......
> I'm not aware which method was used to install Ubuntu on this computer.         
** Look at your /etc/fstab file. If it mentions /host it's a wubi install.
** Based on the_[COLOR=#0000cd] [/COLOR][[COLOR=#0000cd]WubiGuide[/COLOR]]("https://wiki.ubuntu.com/WubiGuide")[COLOR=#0000cd]:[/COLOR]_
> How do I access the Windows drives?

The  Windows partition where you installed Wubi is available as /host within  Ubuntu (Places > Computer > File System > Host) All the other partitions will be available under Places > Removable Media 
If KDE has in fact a "automount at login" for removable drives ( which would have to be looked at in context of Wubi  ) and you have a Wubi install your posts begin to make sense. There would only be references to "/" and swap in fstab and both your ntfs  partitions would mount automatically.

Would mounting these partitions in fstab affect how Wubi / KDE is mounting these drives? I do not know as my lack of experience with KDE is second only to that of Wubi.

---

### Post by GreatBunzinni on 2013-05-31
> **Morbius1 said:**
> 
** Look at your /etc/fstab file. If it mentions /host it's a wubi install.


I've looked at /etc/fstab and there is no "host" string in it.

---

### Post by GreatBunzinni on 2013-05-31
Besides adding entries to fstab, is there any other way Ubuntu and/or Unity can be configured to automatically mount drives?

---

### Post by GreatBunzinni on 2013-06-28
Does anyone care to take a stab at this issue?

---

### Post by Zill on 2013-06-28
> **GreatBunzinni said:**
> Besides adding entries to fstab, is there any other way Ubuntu and/or Unity can be configured to automatically mount drives?
Are you using [Autofs]("https://help.ubuntu.com/community/Autofs")?
> autofs is a program for automatically mounting directories on an as-needed basis. Auto-mounts are mounted only as they are accessed, and are unmounted after a period of inactivity...

---

### Post by GreatBunzinni on 2013-06-28
> **Zill said:**
> Are you using [Autofs]("https://help.ubuntu.com/community/Autofs")?

I don't believe I am.  I've looked for /etc/auto.master and there is no such file in my file system.

---

### Post by GreatBunzinni on 2013-08-30
Update:

After a recent update (sudo apt-get update && sudo apt-get upgrade), the partition which was being mysteriously mounted on /media/DATA is now being mounted instead on /media/$USER/DATA, unleashing all types of hell in the process.

Adding an entry in /etc/fstab to mount the partition back on /media/DATA appears to sidestep this issue.  Nevertheless, it would be nice if it was possible to know how Ubuntu handles these partitions instead of relying on faith and blind luck.

---

### Post by Morbius1 on 2013-08-30
Ubuntu is mounting it the same way it always did but when you upgraded you moved to udisks2. Udisks2 moved the auto-generated mount point from /media/LABEL to /media/$USER/LABEL. Why did they do this? Because they can and because no one ever thinks of the consequences of what they do.

Take a look at the permissions of /media/$USER - and you have to look at permissions this way because at first glance it looks like only root has access to the folder:
```
getfacl -t /media/$USER
```
Only $USER has access to the mount point under /media/$USER regardless of what permissions you set on the mount point itself. 

But anywho, although the mount point changed the process of mounting things when the user doesn't use fstab remains exactly as it was and is not faith-based.

---

### Post by GreatBunzinni on 2013-09-16
> **Morbius1 said:**
> 
But anywho, although the mount point changed the process of mounting things when the user doesn't use fstab remains exactly as it was and is not faith-based.

I expect the mount process not to be faith-based.

But it starts to appear unlikely that it isn't, because the partition was being mounted without any fstab entry, and apparently, from the answers this thread has received, no one actually knows how that is happening.

Thankfully, forcing the mouting process by adding a custom entry to /etc/fstab does appear to side-step this problem.  Yet, as the default mounting process radically changed without any notice, what guarantees that mounting it through /etc/fstab will continue to work?

So, it might not involve faith, but it does appear to be an arcane art.

---

