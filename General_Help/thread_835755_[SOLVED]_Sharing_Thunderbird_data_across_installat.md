---
title: "[SOLVED] Sharing Thunderbird data across installations"
date: 2008-06-20
forum: General Help
---

### Post by yman on 2008-06-20
We have a system set up to dual boot between Vista and Hardy. My dad would like very much if I set it up so that Thunderbird on Ubuntu shares the Thunderbird files on Vista. The question is, how do I make this happen? Is it as simple as a symlink?

---

### Post by Dies on 2008-06-20
It's as simple as pointing Thunderbird to the folders on your Vista partition, you can do this under Account Settings.

If you need help mounting your Vista partition, it's probably already mounted if you accepted the defaults during install, post back.

---

### Post by yman on 2008-06-20
> **Dies said:**
> It's as simple as pointing Thunderbird to the folders on your Vista partition, you can do this under Account Settings.

If you need help mounting your Vista partition, it's probably already mounted if you accepted the defaults during install, post back.

Thanks. However, my problem now is that I don't know where the folder is located at in the NTFS partition.

---

### Post by crossedout on 2008-06-21
Look in:
Documents and Settings\USERNAME\Application Data\Thunderbird\

You'll find your Profiles folder in there.

-Xout

---

### Post by yman on 2008-06-23
> **crossedout said:**
> Look in:
Documents and Settings\USERNAME\Application Data\Thunderbird\

You'll find your Profiles folder in there.

-Xout

It's Vista, so it's different from XP. Did you mean this:
> /media/sda1/Users/Yman/AppData/Roaming/Thunderbird/Profiles/somethingrandom234.default/Mail/Local Folders

Would that contain all mail downloaded from the server? What about filters, folders, and contacts?

---

### Post by Nepherte on 2008-06-23
If you point it to profile directory, it will take over everything from the windows installation. No need to dig into the Mail folder.

---

### Post by nick_h on 2008-06-23
[Howto: Share Thunderbird & Firefox data between Ubuntu & Windows](http://ubuntuforums.org/showthread.php?t=203524)

---

