---
title: "Issues with USB flash drive"
date: 2007-06-11
forum: General Help
---

### Post by jackmc on 2007-06-11
Hey,

I have a problem with using my USB drive. It is using vfat filesystem.

When I delete something, the space doesnt become free. It is irritating, because I'm using it for backups, and if I delete an old backup, the file/folder is deleted, but the space doesn't become available.

Any ideas? I don't have the problem with other USB drives..

PS - it is a flash drive, not a hard drive :)

---

### Post by merlinus on 2007-06-11
You might look for a hidden .trash file, and delete its contents.

-merlin

---

### Post by bishop9226 on 2007-06-11
i think because things are going to a hidden .trash file.  try view -> show hidden files 

you can delete the .trash folder i believe.  but first look at [https://answers.launchpad.net/ubuntu/+question/1904](https://answers.launchpad.net/ubuntu/+question/1904)


---

also...

"To bypass the trash can, just hold down the shift key when you delete something from the USB drive.

So if I have five files that I want to delete. I highlight them using my mouse and the CTRL key on my keyboard (for multiple individual selects). Then, instead of hitting the Delete key by itself, I hold down the SHIFT key and then hit the Delete key. This removes everything from the drive without putting it in the local volume's trash folder."

---

### Post by Bloch on 2007-06-11
This bug is reported here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/12893](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/12893)

It has been around for 2 years and 3 months!!!

---

### Post by jackmc on 2007-06-11
yep, it was the trash. Thanks for the explanation :)

---

### Post by kstella on 2007-06-11
Wow, I was wondering about this. Thanks.

---

