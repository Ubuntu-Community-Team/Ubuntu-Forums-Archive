---
title: "I have a new file in my Wubi folder"
date: 2008-02-01
forum: General Help
---

### Post by stevelasvegas on 2008-02-01
Under the disks folder is a file named .fuse_hidden0000000700000002
which is 6 GB+ in size
How did this get here and how can I safely remove it. It wasn't there yesterday.
Thanks for any help you can give me.

---

### Post by ago on 2008-02-01
That's an autorecovery for a corrupted file(system). It will probably contain recovery info for  one of the wubi disks. If everything you need is already available, then delete it.

---

### Post by stevelasvegas on 2008-02-01
Thanks

---

### Post by ago on 2008-02-02
In fact to be more precise: [http://ubuntuforums.org/showpost.php?p=4180379&postcount=5](http://ubuntuforums.org/showpost.php?p=4180379&postcount=5)

> **szaka said:**
> You can safely ignore .fuse_hiddenXXXX files. It means a file was deleted but there is at least one software which is still using it, so it can't be removed permanently. It will be done automatically when the relevant software stops using the file or exists. Such files are always gone after umount/reboot. This is how Linux and any Unix works but only FUSE exposes these files to the user. In the future we may try to make them unvisible but that's not very simple.

Szaka is the ntfs-3g author

---

### Post by ago on 2008-02-02
It might mbe that if you have a crash, those files do not get removed and stay around.
So my autorecovery explanation was half correct.

---

