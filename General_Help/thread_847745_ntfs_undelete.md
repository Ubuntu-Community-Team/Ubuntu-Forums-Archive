---
title: "ntfs undelete"
date: 2008-07-02
forum: General Help
---

### Post by billwerb on 2008-07-02
I was browsing my Windows XP NTFS partition in Ubuntu and I accidentally deleted a folder in documents and settings (My Documents :(). There was no warning, just everything gone in a couple of seconds after hitting delete.
The question is, obviously, is there anyway of recovering this data. I can't find any trash file in Ubuntu, and Recuva finds nothing in windows.
I do have a back-up, but it's a couple of days old, so I've lost quite a bit of data.
Any help would be much appreciated. 
I sorry for just registering just to ask this question, but extensive googling (my normal answer to Ubuntu probs) came up with nothing :(

---

### Post by untermensch on 2008-07-02
Did you check your trash in Windows? =p And there is no trash in Ubuntu?

---

### Post by billwerb on 2008-07-02
Yes, there is nothing in the windows trash, and I meant the ".Trash-<username>" in the root of the partition.

---

### Post by Habbit on 2008-07-02
As a last resort brute-force method, try to find particular file in the lost directory throughout the FS hierarchy, like this: ```
$ sudo find / | grep "My Pictures"
```

---

### Post by VMC on 2008-07-02
".Trash-<username>" in the root of the partition.
Were you using root when this happened?

You might be able to recover using some Windows  recovery tools, like uneraser. Hiren's Boot CD has a ton of them.

---

