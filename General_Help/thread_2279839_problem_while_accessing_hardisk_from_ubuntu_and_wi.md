---
title: "problem while accessing hardisk from ubuntu and windows dual boot pc"
date: 2015-05-26
forum: General Help
---

### Post by thomas52 on 2015-05-26
hi,
i have installed Ubuntu alongside windows 7 and whenever i boot my computer from Ubuntu i can gain access to my windows files. i don't know how this is possible. 
but  please tell me how to secure my windows 7 files and prevent Ubuntu from gaining access to those files. 

i am using Ubuntu 14.04 LTS version with windows 7 ultimate both are 32 bit operating system.
thanks.

---

### Post by Vladlenin5000 on 2015-05-26
You don't have access unless you mount the partition where the Windows system is installed. You can have another NTFS partition for data only that can be accessed and written to by both systems, just don't do it in the Windows system partition, as already commented in your other thread.

It isn't automatic. Unless you click on it - the launcher icon or at the file manager - it won't be mounted and nothing will change.

---

