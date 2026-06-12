---
title: "How to recover files from an uninstalled wubi installation"
date: 2015-02-06
forum: General Help
---

### Post by ismail5 on 2015-02-06
I installed ubuntu a few months ago using wubi, however it started to freeze a lot lately so I decided to reinstall ubuntu. I moved some files from ubuntu to windows before uninstalling wubi, however after uninstalling wubi I remembered that I forgot to backup my eclipse workspace on ubuntu ](*,).
I didn't reinstall ubuntu yet but the boot option menu no longer shows the ubuntu option and I cannot see any linux partitions using ext2explore.

EDIT: Solved: After doing some research, I found only one recovery tool that was successful in recovering my root.disk file, it's called r-studio, I used it to recover my root.disk file then I used ext2explore to open the file and save my workspace.

---

### Post by Mark Phelps on 2015-02-06
WUBI is installed INSIDE an existing Windows filesystem (usually NTFS) in a single file -- root.disk. You won't see any Linux partition because there isn't any. Thus, you need the original root.disk in order to recover files from it.

If you have that, what I've heard does work in some situations is the following:
1) Back off any existing Linux installation
2) Reinstall WUBI -- this creates a new root.disk file
3) Copy the saved old root.disk file over the new root.disk file
4) Launch Ubuntu from WUBI 

If this works, you will see your former files and folders -- and can then retrieve them.

---

### Post by oldfred on 2015-02-06
If root.disk exists, you can just mount it from live installer. You have to also mount the NTFS partition first.

[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

If you have not used Windows much, and file was deleted you may be able to recover file. But it is large and usually Windows will reuse space fairly quickly. If any part overwritten then it would not be recoverable.

---

