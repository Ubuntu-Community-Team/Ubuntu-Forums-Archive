---
title: "possible bugfix"
date: 2007-06-19
forum: General Help
---

### Post by CrazyGuy123 on 2007-06-19
Chances of corruption in disk images during use and on hard reboots seems reduced  (though not eliminated), if the file size for disk images is a multiple of the sector size.

Could I suggest this change, so we can see if it has a significant effect on reducing corruption for others:

line 366 of /src/plugins/diskimage/main.c:
file_pos = EnlargedIntegerMultiply(size, (1<<20)-1); 

line 385:
result = call_SetFileValidData(file, ((LONGLONG)size)*(1<<20)-1); 

Note that if we use real numbers of GB for disk drives (ie base 1024), for the case of a 4GB image file on fat32, it needs to be (4<<30)-(1<<9)  (1 sector less than 4GB) - at the moment numbers in thousands of meg are used in /src/inspector/detect_disk_space.nsh - using real GB numbers might seem more logical to users when they compare disk space used/left on the host and virtual drives.

Apologies for not using the bug tracker - don't have an account there.

---

### Post by ago on 2007-06-19
Thanks a lot, it's a bit late now but we'll add it in next build which will be available in the coming days. If you apply to the lupin-team I will give you direct access to the branch, so you will be able to commit.

---

### Post by ago on 2007-06-26
> **CrazyGuy123 said:**
> Chances of corruption in disk images during use and on hard reboots seems reduced  (though not eliminated), if the file size for disk images is a multiple of the sector size.

Could I suggest this change, so we can see if it has a significant effect on reducing corruption for others:

line 366 of /src/plugins/diskimage/main.c:
file_pos = EnlargedIntegerMultiply(size, (1<<20)-1); 

line 385:
result = call_SetFileValidData(file, ((LONGLONG)size)*(1<<20)-1); 


Any particular reason for the -1?

---

