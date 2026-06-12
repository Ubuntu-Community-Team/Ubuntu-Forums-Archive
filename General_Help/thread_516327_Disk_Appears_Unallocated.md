---
title: "Disk Appears Unallocated"
date: 2007-08-03
forum: General Help
---

### Post by mikaelsnavy on 2007-08-03
Hello,
My hard drive has appeared allocated for a while. Ubuntu (7) could still see all my partitions and access the files, but in gparted the disk looks unallocated. Also, I couldn't boot into windows (i had a working dual boot) This wasnt a horribly big deal until i decided to let windows try to fix it. It erased grub and it didnt fix windows. Now, i try to re-install grub, but it doesnt detect any partitions. I just want to get back into ubuntu.
Thanks,
Mikael

---

### Post by merlinus on 2007-08-03
You might try SuperGrub.  Info here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by jet2230 on 2007-08-03
1000's of solutions here: [http://www.google.co.uk/search?q=fix+grub&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=fix+grub&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

quick fix: 
1) boot from live ubuntu cd
2) open terminal window, run 'grub'
3) type 'find /boot/grub/stage1'   - keep eye on result*
4) type 'setup (hd0)' - ( where hd0 = whatever your result was)
5) type 'quit'
6) restart

---

### Post by mikaelsnavy on 2007-08-03
jet2230, I tried that and I get "Error 15: File not Found". It is because of the partition table errors.

Then I 

merlinus, I am about to try supergrub

---

### Post by mikaelsnavy on 2007-08-03
supergrub didnt work either.
It couldnt boot or do anything!!!

---

### Post by mikaelsnavy on 2007-08-03
If it helps,Vista repair cannot detect vista. I think it is a partition table error.

---

