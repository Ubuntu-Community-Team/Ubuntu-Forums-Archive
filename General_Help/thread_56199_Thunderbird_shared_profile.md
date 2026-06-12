---
title: "Thunderbird shared profile"
date: 2005-08-11
forum: General Help
---

### Post by pompeyjohn on 2005-08-11
Hello,

I am a bit new to all this, so please be gentle. I have searched the forums, but not found anything applicable - apologies if I have missed something. 

I have a drive set up as follows

hda1... ntfs
hda2... ext3
hda3... swap
hda4... fat32

Quite a common setup I expect. Well, I'd like to share the tb & ff profiles used in XP with Ubuntu. I have set both of them in XP to run from profiles stored in a directory on the fat32 drive. I have then automounted the drive in fstab using the following:

/dev/hda4       /shared		vfat    iocharset=utf8,umask=000   0       0

That appeared to work fine, I could say the profiles directory in konqueror.. However, when I open up the TB profile manager it can see the mounted drive, but none of the folders on directories it contains.

So first of all, what is happening there? Secondly, once the TB profile manager can see the profile directory how do I link to the existing profile? Is it simple create a new profile and then point to an existing particular file or folder? I am guessing it is, but obviously have not got that far yet.

Thanks in advance,

John

---

### Post by aveline on 2005-08-11
[QUOTE=pompeyjohn]Hello,

I am a bit new to all this, so please be gentle. I have searched the forums, but not found anything applicable - apologies if I have missed something. 

I have a drive set up as follows

hda1... ntfs
hda2... ext3
hda3... swap
hda4... fat32

Quite a common setup I expect. Well, I'd like to share the tb & ff profiles used in XP with Ubuntu. I have set both of them in XP to run from profiles stored in a directory on the fat32 drive. I have then automounted the drive in fstab using the following:

/dev/hda4       /shared		vfat    iocharset=utf8,umask=000   0       0

That appeared to work fine, I could say the profiles directory in konqueror.. However, when I open up the TB profile manager it can see the mounted drive, but none of the folders on directories it contains.

So first of all, what is happening there? Secondly, once the TB profile manager can see the profile directory how do I link to the existing profile? Is it simple create a new profile and then point to an existing particular file or folder? I am guessing it is, but obviously have not got that far yet.

Thanks in advance,

John[/QUOTE]
 i found a way once to share my profile tween windows xp & linux but for the life of me i can't find how to it again...also i do know you need to install tb onto a fat32 partition for this idea to work.

aveline

---

### Post by pompeyjohn on 2005-08-12
thanks aveline - have the fat32 setup,... anyone else have an idea about what is going on??  :smile:

---

### Post by Owdy on 2005-11-09
Im trying to do same. With FF and TB

---

### Post by popeye on 2005-11-13
Hi,

Be sure thunderbird is not open.

```
 gedit /home/youruser/.mozilla-thunderbird/profiles.ini
```

find IsRelative and change it to 0
IsRelative=0

find Path and change it to your profile location
Path=/shared/profilelocation/profilecode.default

i have this:
> /dev/hda2      /shared  vfat     umask=0000
in /etc/fstab

and this worked fine for me.

[http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location](http://kb.mozillazine.org/Thunderbird_:_FAQs_:_Changing_Profile_Folder_Location)

---

