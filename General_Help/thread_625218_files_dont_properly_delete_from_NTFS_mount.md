---
title: "files dont properly delete from NTFS mount"
date: 2007-11-27
forum: General Help
---

### Post by Zyren on 2007-11-27
I have a 400gb external hard drive thats formatted in NTFS. Ubuntu mounts it fine, but whenever i delete files and "move to trash," it doesnt make more free space. There is nothing in the trash bin either. It keeps saying i have 1gb free space when i just deleted about 5gb of files. i tried unmounting and remounting and it still says 1gb free. The files that i deleted are also not showing in the file browser. 

anyone know why it is doing this? I am using gutsy and as far as i know it has NTFS read/write support built in the OS.

---

### Post by hardyn on 2007-11-27
it now has the ability to be read/write, but im not sure that it is enabled by default.  the way that it is behaving would suggest that write support is NOT enabled.

---

### Post by jayde6 on 2007-11-27
On moun'ted partitions like that it puts the files in a '.trash-(name of partition)' folder. Push 'Control-H on the partition and you should see it. You can delete that folder and the files will be permanantly gone.

---

### Post by Jazmo on 2007-11-29
> **jayde6 said:**
> On moun'ted partitions like that it puts the files in a '.trash-(name of partition)' folder. Push 'Control-H on the partition and you should see it. You can delete that folder and the files will be permanantly gone.

Isn't that stupid? Why hide files from user that way? The Trash itself is a good idea but why it is not visible to users?

But thankyou, that helped me.

---

### Post by FuturePilot on 2007-11-29
> **Jazmo said:**
> Isn't that stupid? Why hide files from user that way? The Trash itself is a good idea but why it is not visible to users?

But thankyou, that helped me.

That's how it works, you even have a .Trash folder in your home directory. However there seems to be a glitch with NTFS drives as anything deleted from the drive will not show up in the trash.

---

