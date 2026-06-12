---
title: "move the temporary downloading files to another partition"
date: 2007-08-27
forum: General Help
---

### Post by chunchengch on 2007-08-27
When I use MultiGet to download archives, MultiGet creates and stores the temporary files automatically in the hiding folder ./MultiGet under the root, I wonder if it is possible to make MultiGet create and store the temporary files in another folder in another partition?

---

### Post by vanadium on 2007-08-27
I do not know MultiGet, but I know how to achieve what you want using the operating system: that is a powerfull beast! Create a directory Multiget where you want the files to download. Then copy all contents of the current Multiget directory to that new one (these might include settings). Finally, delete the original Multiget directory, but create a symbolic link with exactly the same name that refers to the new Multiget directory. The symbolic link will behave exactly as if it were a real directory. In other words: Multiget will work as if nothing happened.

---

### Post by chunchengch on 2007-08-27
vanadium,

Thanks a lot! it works.:)

---

