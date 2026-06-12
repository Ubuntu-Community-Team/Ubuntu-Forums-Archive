---
title: "Deleted file containing bitcoin seed key trying to find it with testdisk but can't"
date: 2016-09-24
forum: General Help
---

### Post by sportscrazed2 on 2016-09-24
Can someone please help me?  It's like trying to find a needle in a haystack after running the program a few times and cancelling to try and get it right. Is there any other program that can recover data by searching for it?  BTW it's on an ntfs external drive if that helps

---

### Post by DuckHook on 2016-09-24
You did not back up such a critical file???

NTFS is a Windows filesystem. You should use Windows tools to try to retrieve it. The general rule: "use Linux tools for Linux files; Windows tools for Windows files" applies here. Do not use that disk any further. Especially do not write anything to it.

Because you use NTFS, I assume you dual boot into a Windows OS. I stopped using Windows years ago, so no longer have any familiarity with it. Others will have to help you in actual use of Windows tools. Have you tried the Windows forums?

---

### Post by sportscrazed2 on 2016-09-24
> **DuckHook said:**
> You did not back up such a critical file???

NTFS is a Windows filesystem. You should use Windows tools to try to retrieve it. The general rule: "use Linux tools for Linux files; Windows tools for Windows files" applies here. Do not use that disk any further. Especially do not write anything to it.

Because you use NTFS, I assume you dual boot into a Windows OS. I stopped using Windows years ago, so no longer have any familiarity with it. Others will have to help you in actual use of Windows tools. Have you tried the Windows forums?

I used linux to delete it though

---

### Post by DuckHook on 2016-09-24
> **sportscrazed2 said:**
> I used linux to delete it thoughIt doesn't matter what OS erases the file. All HDD deletions are done by simply erasing the reference to the file in the MFT. This is an easy process, so a Linux OS can do this no problem. But when you are trying to restore a file to the MFT, this is complicated and potentially dangerous process. It requires the recovery software to delve into the guts of the file-structure to first find the file, then rebuild its reference in the MFT. Linux developers know Linux file-structures like the back of their hand and so make the best tools for Linux file-systems. Likewise on the Windows side.

Below is a link to various NTFS tools. I advise you to do this salvage operation from the Windows side.

[http://ntfs.com/products_win_bootdisk.htm](http://ntfs.com/products_win_bootdisk.htm)

---

