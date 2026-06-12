---
title: "What is / are resons for differet foldder for mount points?"
date: 2020-10-29
forum: General Help
---

### Post by helen314 on 2020-10-29
I started using "Disks" to control mount points.
( I have another post but it covers SPECIFIC and different  issue,) 


I am posting this  here to confirm this 

```

/media is for users and /mnt is for admins

```

That is pretty terse and does no really explain 

1. **why ** is there a need for separating admin and user by mounting points?
    If it is yet another "Linux security"  no elaboration is necessary, just state so.
2. "Disks"  is run under administrator = user , s**o why** when assigning mount point using :"name" I get
 **   /mount**/a/  <mount point name > using SIMPLE mount point?
    BTW I have no control about WHAT method - name or UUID Disks picks.
3**. When adding** "name=...."  to "Disks "  option I end up with 
   ** /mnt**/ < mount point. by UUID > 

Results 
I can retrieve files using "Files" using name of the mount point
oir
I can retrieve files via  /mnt     folder using UUID .

---

### Post by CatKiller on 2020-10-29
That description you posted isn't really accurate. Traditionally, and reflected in the behaviour of desktop environments, /media is for *removable media* like cds, dvds, thumb drives, and so on. /mnt is generally used for semi-permanently mounted filesystems that aren't mounted to one of the *functional* places in the filesystem tree.

You can mount whatever you want wherever makes the most sense to you: it's your system.

I don't use Gnome, so I don't use Gnome Disks, but people that have suggest that it makes some questionable choices. I would generally just set up fstab for any filesystems that I wanted to be mounted. It's a fairly straightforward text file.

---

### Post by helen314 on 2020-10-30
> **CatKiller said:**
> That description you posted isn't really accurate. Traditionally, and reflected in the behaviour of desktop environments, /media is for *removable media* like cds, dvds, thumb drives, and so on. /mnt is generally used for semi-permanently mounted filesystems that aren't mounted to one of the *functional* places in the filesystem tree.

You can mount whatever you want wherever makes the most sense to you: it's your system.

I don't use Gnome, so I don't use Gnome Disks, but people that have suggest that it makes some questionable choices. I would generally just set up fstab for any filesystems that I wanted to be mounted. It's a fairly straightforward text file.

Thanks for the replay.

As I eluded - if I have hard drives  with USB interface - is it "removable device" ?
I was running some test, do no recall which one, but it "asked"  is such a such removable device?  - it was checking hard drive with SATA 
interface. 

I am not concerned with definitions , but like some logical consistency based on some , preferably defined, criteria. 

AS far as fstab - this has been one of the most "guess how this works"  tool - mainly the disarray of options , depending 
whom you ask style. I have found usage of "LABEL="  early on , unfortunately  it seems to be rarity. 
What "Disks" passes to fstab is IMHO unreal mess.

BUT - it takes some experience to be able to deal with "fstab" directly.

---

### Post by SeijiSensei on 2020-10-30
I mount the NFS filesystems exported from my server under /media. These days I only use /mnt for temporary mounts. As CatKiller says, these decisions are largely arbitrary.  All the mount points are owned by root; access to the remote files relies entirely on the standard user and group method. The lists of users and groups on my client machines match the contents of the server's /etc/passwd and /etc/group files.

---

### Post by deadflowr on 2020-10-30
A removable device is anything that can be detached from the system at any point and will not cause any issues with the running system.
Be it a drive from a usb or a partition on the same disk that the OS is on.

---

### Post by rsteinmetz70112 on 2020-10-30
> **helen314 said:**
> Thanks for the replay.

AS far as fstab - this has been one of the most "guess how this works"  tool - mainly the disarray of options , depending 
whom you ask style. I have found usage of "LABEL="  early on , unfortunately  it seems to be rarity. 
What "Disks" passes to fstab is IMHO unreal mess.

BUT - it takes some experience to be able to deal with "fstab" directly.

I use Gnome Disks all the time to look at disks and get information. I do not use it for configuring things. /etc/fstab is not really that complicated, it just looks that way. I find that "defaults" works well for most common situations except the root filesystem. The great thing about *nix is that every one has an opinion. :cool:

---

### Post by CatKiller on 2020-10-30
> **helen314 said:**
> if I have hard drives  with USB interface - is it "removable device" ? 

The primary distinction is whether you think it should automatically get an icon on the desktop. If it should, mount it in /media; otherwise, mount it somewhere else. 

> AS far as fstab - this has been one of the most "guess how this works"  tool - mainly the disarray of options , depending 
whom you ask style.

**man fstab** says exactly how it works.

---

### Post by helen314 on 2020-11-02
**man fstab** says exactly how it works. 				

Agreed.
I but I was referring to sequence of the options, added by tools likes "Disks".



Here is a clarification to the original question 

An application - suchj as "Disks" , running under user 
adds 
/mnt/ <UUID >      mount point 

or 
/media/user/<UUID>  mount point 


and there is no difference  between them?

---

### Post by oldfred on 2020-11-02
One difference is /media will be shown in Nautilus, not sure about other browsers.

And /mnt will not be shown in Nautilus, you have to drill down(up) from / to find /mnt.
But I use /mnt for my data partition, as I link all my folders in my data partition into /home as I want each folder shown, not just one entry. Others suggest just using / if linking and not using /mnt.[[IMG]https://ubuntuforums.org/clear.gif[/IMG]]("https://ubuntuforums.org/editpost.php?p=13997293&do=editpost")

---

