---
title: "cant get past &quot;prepare disk space&quot;"
date: 2007-02-06
forum: General Help
---

### Post by SpiffyChee on 2007-02-06
im trying to install xubuntu (actually ive tried all the ubuntu type linuxs) and they wont get past the prepare disk space step. I resize the partition and click forward and it loads forever and i eventually have to cancell it. The harddrive already had win xp on it and i dont want to reinstall windows. how do i get ubuntu on my laptop? help plzz

---

### Post by etank on 2007-02-07
I have had some trouble in the past with using the LiveCD to do installs. Try downloading the Alternate install CD. It doesn't use a gui for the install but it works very well.

---

### Post by SpiffyChee on 2007-02-07
how do i make sure with the non live install that it wont delete my windows xp?

---

### Post by eggdeng on 2007-02-07
The version of the gparted partioning utility on the install cds is buggy. Download the latest gparted live cd from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and just do all your partitioning & resizing before you start installation. It really is an essential, powerful & versatile tool.

---

### Post by SpiffyChee on 2007-02-07
go gparted will let me resize my single hard drive with windows to one for windows and one for linux without deleting my windows stuff? and will it still boot into it?

---

### Post by bodhi.zazen on 2007-02-07
Yes, but defragment you windowsw partition first.

And, although rare, back up any data you do not want to lose ...

---

### Post by SpiffyChee on 2007-02-07
defrag within windows in the controll panel? how is that done?

---

### Post by bodhi.zazen on 2007-02-07
In Windows:

Start -> All Programs -> Accessories -> System Tools -> Disk defragmenter :)

---

### Post by Skidpad on 2007-02-07
Laptop? I had the same problem...it was my XP page & hibernation files that were unmovable on my XP partition.  Read the first link for the nature & solution to my problem, or skip straight to the second link for the solution.
 [http://www.ubuntuforums.org/showthread.php?t=327923]("http://www.ubuntuforums.org/showthread.php?t=327923")

Scroll down to "Moving the unmovable":
[http://www.ubuntuforums.org/showthread.php?t=327923]("http://www.ubuntuforums.org/showthread.php?t=327923")

Cheers

---

### Post by SpiffyChee on 2007-02-08
haha that must have done it. thanks!!!!
(just curious, what is defraging actually doing?)

---

### Post by Skidpad on 2007-02-08
> **SpiffyChee said:**
> haha that must have done it. thanks!!!!
(just curious, what is defraging actually doing?)
Glad it worked for you. \\:D/ 

Defragging attempts to reorganize & consolidate the various bits and pieces of information that make up a complete file.  When Windows writes information to disk, it doesn't write it in a continuous manner - the bits and pieces are written on the fly where they fit at the time, and the whole file ends up scattered all over the place.

Defragmentation is the act of attempting to puts all of these bits and pieces of files together for faster, consistent performance.

---

