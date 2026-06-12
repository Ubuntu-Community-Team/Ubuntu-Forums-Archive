---
title: "Which files are required for a bootable Live-CD?"
date: 2007-09-17
forum: General Help
---

### Post by mojo on 2007-09-17
My aim is to customize a Live-CD in which installation feature and other extra folders are to be deprecated. As I am aware of, the content of Live-CD of any Ubuntu version is like this:

-bin
-casper
-disctree
-dists
-install
-isolinux
-pics
-pool
-preseed
-programs
autorun.inf
md5sum.txt
README.diskdefines
start.bmp
start.exe
start.ini
ubuntu.ico

After doing some research, I found it is safe to remove:
-bin
-programs
autorun.inf
start.bmp
start.exe
start.ini
ubuntu.ico

So, can I delete more folders? Tell me if it's safe to remove:
-disctree
-install (In my case, I dun want memtest and sbm)
-pics
-dists (again, my aim is to remove installer part of LiveCD)
-pool
-preseed (seems to me isolinux.cfg uses the ubuntu.cli inside this folder)

And can someone tell me what preseed is? Thank you so much in advance.

---

