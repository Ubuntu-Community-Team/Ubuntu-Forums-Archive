---
title: "USB storage device=&quot;read only file&quot;"
date: 2007-05-18
forum: General Help
---

### Post by SaintRatho on 2007-05-18
OK, I'm pretty new to Kubuntu. My buddie got me hooked on it. My issue is that my USB storage device is not allowing me to access the files. I can open them, but can not save any items into it or delete from it. When I try to put something such as the Kubuntu ISO file on it (yes I have space) it tells me ERROR: "You do not have permissions to write to this folder" So I decided to try deleting a file from it. On the right click drop down the "move to trash option is grey and I can't use it" So then I tried to drag & drop a file into the trash. Then I get ERROR: "Unable to move to trash:
Read only file system" I am thinking I may have corrupted my USB, but not sure if I just did something else wrong. I was raised on Windows and am not used to haveing acessability to make things REALLY run. Windows=Windows error:mad:, Linux/Ubuntu etc= User Error. :confused:

Please let me know if you have a solution. 

PS- I confess I did remove the USB without ejecting once, then this happened. I don't remember if it was happening before this though. 

Thank you for any help you can provide. You guys ROCK! :guitar:

---

### Post by dfreer on 2007-05-18
The problem is almost for sure to be that you are using NTFS on that external hard drive. Ubuntu cannot natively write to a NTFS Partition. So now you have about 3 different options:

Install NTFS3G driver so that you can read/write to NTFS.
Use a shared FAT32 drive to move data from one OS to another, by shrinking the NTFS partition.
Reformat the partition.

I have never installed NTFS3G myself (due to running linux only :D ), so I cannot help you there. I know there is a debian package for it, and TONS of threads/posts on this forum about installing it. Also tons of threads already about not being able to write to external USB due to read only error, but that's ok searches don't always work, especially when you don't know what the problem is. Good luck with linux/ubuntu and welcome!

EDIT: Of course, if you aren't using NTFS and were able to write to it before, my apologies. Post your /etc/fstab and /etc/mtab file if this is the case so we can see how the USB hard drive is being mounted.

---

