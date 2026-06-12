---
title: "Formatted RAID, Data Recovery"
date: 2008-02-05
forum: General Help
---

### Post by Ryoojin83 on 2008-02-05
I was an idiot...

I have a Software RAID 5 array with 4x500GB HDDs.
I installed a new system and I was getting fed up with having to reassemble the RAID every time I booted into the new system.  I used to be a gentoo user and on my old gentoo machines I just recreated the array like it was going to be new, and all my data was kept. 
'mdadm -C /dev/md2 -n4 -l5 <drives>'
Well, I did this and it started the array but I couldn't mount it...but instead of doing fsck like I should have done, I was an idiot and typed mkfs.ext3... yeah, duh.. well, now here I am with 1.4T of no data.   

Is it possible to recover this data?  

sorry for the broad question, but I am kind of freaking out right now, since I just lost about 7 years worth of data....

---

### Post by solitaire on 2008-02-05
Yes it's possible

but i only know of Windows based Software to do it.

[http://www.runtime.org/raid.htm](http://www.runtime.org/raid.htm)

Their will probably a load of Linux solutions but I don't know any off hand..

---

### Post by Ryoojin83 on 2008-02-05
Thats hard seeing as I don't have an extra terabyte to store the data on.
I used to use a program called easy recovery pro for windows, it was nice, it read the RAW data on the drive and made its own list of files and locations when let you choose what files you wanted.

is there anything similar in linux?

---

