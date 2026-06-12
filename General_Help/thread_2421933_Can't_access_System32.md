---
title: "Can't access System32"
date: 2019-06-29
forum: General Help
---

### Post by saruman5679 on 2019-06-29
So, I'm pretty new to Linux, correct me if I get anything wrong. I'm using a live version of Ubuntu booted from a USB drive on a computer that I normally run Windows 10 from. I mounted my Windows partition and tried to open the System32 file, but was faced with a 'this location could not be displayed' message, saying it had encountered trouble while getting information for a file named 'bthci.dll'. It specifies that it's an input/output error but I can't discern what could be wrong. Any help would be greatly appreciated. I can also upload a screenshot if necessary.

Thanks in advance.

---

### Post by Artim on 2019-06-29
Ubuntu's file system may not have access to those files because you have to be "Administrator" (in Linux we call it "root") to do it.  Try doing it as root.

---

### Post by Impavidus on 2019-06-29
First of all, when fast startup (or fast boot, I always confuse them) is enabled on Windows, it doesn't cleanly unmount the filesystem. That allows Windows to restart faster, but blocks access to its filesystem by other systems. Shut down Windows completely or try to mount the filesystem read-only, which may work.

However, you suggest that you managed to mount the filesystem and see the presence of some files, but cannot access those files. It's probably filesystem damage, although a broken hard drive cannot be ruled out. Linux cannot fix broken Windows filesystems other than some very basic repairs. A Windows repair disk may help.

---

