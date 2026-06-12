---
title: "Gutsy Freezing"
date: 2007-12-10
forum: General Help
---

### Post by bortolozzi on 2007-12-10
Hi all,

I have Gutsy installed on a “Toshiba Satellite P205-S6337” Notebook. The installation (in dual boot with Windows Vista, previously installed) was very easy and almost everything was detected and set up with no big problem. Even Compiz effects are working perfectly well.

The problem is that, every once in a while, it just freezes. Only the mouse cursor continues to work. Everything else stop responding and I need to force a restart.

Any tips of what can I do to solve this problem? Any kind of logs, or something else, that I could check to see the reason of this freezing?

That's how the disk is partitioned: 10 GB for Ubuntu, 1GB for swap and 180 GB for NTFS.

Thanks in advance,
Juliano

---

### Post by Portable_Jim on 2007-12-10
It might be that Ubuntu is not recognizing the swap space. That's what it was when I had the same symptoms. 

To see type into the temrinal: ```
free
``` and see if there is any swap space (when the first number in the last line > 0)

---

### Post by bortolozzi on 2007-12-10
It is recognizing the swap space, although, now, nothing is used (1GB, 0 used).

Thanks anyway,
Juliano

---

### Post by bortolozzi on 2007-12-10
Although it has recognized the swap memory,  I don't know if the problem is happening right when Ubuntu is trying to use it. What did you do to fix the problem?

Thanks again,
Juliano

---

### Post by Portable_Jim on 2007-12-10
I had to add the swap partition to my fstab so that Ubuntu would recognize my swap space (it was also on an earlier version of Ubuntu).

Because it is 
recognizing the swap space on your computer, I am not sure what would be wrong.

---

### Post by bortolozzi on 2007-12-19
All,

I noticed that I never use my swap partition. Ubuntu freezes before that. (I have 2Gb of memory)

I also noticed that the freeze starts more often in some applications, like Mono Develop (I never can use it for more than 10 mins), K3B and Firefox, in some web sites with too many client scripts.

Any idea?

Thanks for your help
Juliano

---

### Post by bortolozzi on 2008-01-15
new information: Since I disabled Compiz, it never freesed again. So, the problem seems to be caused by Compiz, or even the video card driver.

---

### Post by whaase on 2008-02-02
If you are using a Nvidia driver, try this:

Open the startscript for Compiz:

sudo gedit /usr/bin/compiz


look for the line about "No indirect by default" and change it to

INDIRECT=0

---

