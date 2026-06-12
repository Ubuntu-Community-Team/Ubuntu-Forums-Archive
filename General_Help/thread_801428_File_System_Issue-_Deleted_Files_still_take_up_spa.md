---
title: "File System Issue- Deleted Files still take up space"
date: 2008-05-20
forum: General Help
---

### Post by yakolev on 2008-05-20
I recently copied a large set of files onto my partition, had the process interrupted and so deleted the incomplete attempt in a superuser nautilus, emptied the trash and then copied the files again, however....
It still thinks that the 40 gigabytes from the previous attempt are still being used, both in disk-usage analyzer and nautilus. I have checked numerous time in /root/.local/share/Trash/files and even performed an rm -rf in that directory but the space is still being taken up.

I haven't tried fsck yet, I will but I suspect it won't resolve this.

---

### Post by drs305 on 2008-05-20
> **yakolev said:**
> I recently copied a large set of files onto my partition, had the process interrupted and so deleted the incomplete attempt in a superuser nautilus, emptied the trash and then copied the files again, however....
It still thinks that the 40 gigabytes from the previous attempt are still being used, both in disk-usage analyzer and nautilus. I have checked numerous time in /root/.local/share/Trash/files and even performed an rm -rf in that directory but the space is still being taken up.

I haven't tried fsck yet, I will but I suspect it won't resolve this.

We you in root when you were originally copying the files. Root has a trash folder different from users. You would have to make sure that you deleted the trash in the correct account.

```
sudo find /home/username/.local/share/Trash
```
```
sudo find /root/.local/share/Trash
```

---

### Post by insomnica on 2008-05-20
Have you tried clearing the Wastebasket via the Delete Items folder?
Everything is worth a try I guess.

---

### Post by jjgomera on 2008-05-20
how much memory do you miss? about 5% of total partition memory

---

### Post by yakolev on 2008-05-20
This is about a third of the entire partition. I understand that the ext3 file system itself takes up space.

I have deleted using the gui as the root user by opening nautilus with gksudo. The files were there, in the root user's wastebasket. I deleted them from there using the gui, and they are still taking up space. I ran rm -rf /root/.local/share/Trash/files/* after presuming it empty and they still took up space. In the actual user I emptied the trash and found this directory empty.

Disk usage anylzer and nautilus report 80 gigs used instead of 40 even though the whole of / is only 40 by all counts.

---

### Post by yakolev on 2008-05-20
Also I just ran fsck on the partition to no avail.
And deleted the contents of the "info" folder as well as just the files folder in Trash, which did contain files relating to the ones I deleted.
Also to no avail, the thing still reports / as being 40gb and that 80gib of the partition are being used.

---

### Post by yakolev on 2008-05-20
This screenshot might convey the bafflement a hair better

---

### Post by drs305 on 2008-05-21
> **yakolev said:**
> 
Disk usage anylzer and nautilus report 80 gigs used instead of 40 even though the whole of / is only 40 by all counts.

I have found this app somewhat misleading - often new users of DUA think their home folder is full because of the way it displays things. The 

Since your partition size is reported almost double, try Edit Preferences and uncheck the .gvfs directory, if it is listed. It's a network thing and will incorrectly report actual file usage since it includes network mounts.

Second, run the following command. It will tell you what space you actually have left on each of your partitions. 
```
df -Th
```
 
gnome-system-monitor will give you the same information graphically.

---

### Post by yakolev on 2008-05-21
Ah Thanks! This seems to have revealed my panic to be about nothing. The drive is only 80gb, unlike a similar machine of mine with a larger drive which for some reason I thought was in this one as DUA reported it as being larger than it is and I confused the two and so there we are.

---

