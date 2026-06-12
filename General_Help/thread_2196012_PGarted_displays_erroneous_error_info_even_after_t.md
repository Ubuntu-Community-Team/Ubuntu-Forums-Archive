---
title: "PGarted displays erroneous error info even after the hard drive was replaced"
date: 2013-12-27
forum: General Help
---

### Post by Cavsfan on 2013-12-27
I'm just curious about this. Why would gparted still say I have bad sectors on a 500GB hard drive that was installed yesterday.
The old hard drive had 6 bad sectors and 3 sectors were pending, which is what a program in Windows 7 called Speccy showed.
In that program, listed next to the C: S.M.A.R.T drive a status of "Warning" was displayed.
I found this was listed as Warning because the pending bad sector count was greater than zero. It is now zero as well as the bad sector count; it is also zero.

I had opened this thread and went to add to it since I replaced the drive but that thread is closed.

[http://ubuntuforums.org/showthread.php?t=2070792](http://ubuntuforums.org/showthread.php?t=2070792)

Anyway, if the C: drive in Ubuntu/Mint etc. is _unmounted_ gparted shows this

[ATTACH=CONFIG]248940[/ATTACH]

But, when _mounted_ it shows A-OK in Gparted:

[ATTACH=CONFIG]248941[/ATTACH]

In windows 7 running Speccy it shows the status of C: drive is "Good" (no bad sectors and no pending bad sectors).

I just don't understand why Linux would say there is bad sectors when there is none. And why does the error go away when C: is mounted. :???:

---

### Post by Cavsfan on 2014-01-09
When I start Gparted I noticed it says "C: connected" but not "C: mounted" then It gets that error. If I click on C: to mount it then bring up Gparted there is no error.
Odd.

---

