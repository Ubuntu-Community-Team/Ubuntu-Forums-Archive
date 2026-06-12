---
title: "Yet another USB Problem with Gutsy Gibbon."
date: 2007-11-03
forum: General Help
---

### Post by suchawato on 2007-11-03
Ok.
So.
I have a LaCie external hard drive that I received as part of my media kit for school.
At first, I could not read or write to it as Gutsy annoyingly made it a Root only permission by default. This was really irritating, but not unfixable.
Then, after I changed the permissions so that all users could read/write/delete/change files, it seemed to work fine.
Then, the other day when I tried to copy my school assignment to the school folder on my LaCie, it (Gutsy) would not let me. "Access Denied; you don't have permissions to write to this folder". When I used ```
gksudo nautilus
``` to try to re-change the permissions as Root, I got; "The Owner Could Not Be Changed; Couldn't change the owner of "LaCie" because it is on a read-only disk".
There is no switch or button on the LaCie, that makes it "read only".
It's a USB external drive. There would be no point in making it "read only"
It **Isn't** read only.
I don't care what Gutsy thinks.
I can access it fine on the Macs at school.
Gutsy is full of sh!t.

Anybody have any idea how to fix this?
Or should I add it to the stack of so-far unfixable USB problems with Gutsy?
Like iPods not mounting and such.
-Stu

---

### Post by suchawato on 2007-11-03
By the way,,
To the Developers:
It would be *really* nice to have an update that fixes these USB problems Right-away. like ASAP.

---

### Post by dcstar on 2007-11-03
> **suchawato said:**
> Ok.
So.
I have a LaCie external hard drive that I received as part of my media kit for school.
At first, I could not read or write to it as Gutsy annoyingly made it a Root only permission by default. This was really irritating, but not unfixable.
Then, after I changed the permissions so that all users could read/write/delete/change files, it seemed to work fine.
Then, the other day when I tried to copy my school assignment to the school folder on my LaCie, it (Gutsy) would not let me. "Access Denied; you don't have permissions to write to this folder". When I used ```
gksudo nautilus
``` to try to re-change the permissions as Root, I got; "The Owner Could Not Be Changed; Couldn't change the owner of "LaCie" because it is on a read-only disk".
There is no switch or button on the LaCie, that makes it "read only".
It's a USB external drive. There would be no point in making it "read only"
It **Isn't** read only.
I don't care what Gutsy thinks.
I can access it fine on the Macs at school.
Gutsy is full of sh!t.

Anybody have any idea how to fix this?
Or should I add it to the stack of so-far unfixable USB problems with Gutsy?
Like iPods not mounting and such.
-Stu

Is it a NTFS partition, if so have you installed the ntfs-3g package?

---

### Post by suchawato on 2007-11-03
It's not a partition.
It's an external USB drive.
I have no idea how it's formatted.

---

### Post by suchawato on 2007-11-03
OK, so I checked the documentation,
apparently it's formatted in HFS+.
Which explains why it hasn't had any trouble on a Mac.
However, I want to note, that I have been using it fine, on this computer until a couple of days ago.
The format explains why windows doesn't recognize it though. But not why Gutsy suddenly stopped when it was working before.

On a side note, does anyone know of a format that both Windows, Unix/Linux, and Mac will automatically recognize?

---

### Post by PmDematagoda on 2007-11-03
Why don't you try a filesystem like FAT32.

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Fat 32 has had reported problems with Gutsy.
I may give it a try anyway though.

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				the other bug link:

---

