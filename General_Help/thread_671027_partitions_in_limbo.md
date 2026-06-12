---
title: "partitions in limbo"
date: 2008-01-18
forum: General Help
---

### Post by Smbrandes on 2008-01-18
I suffered an idiocy today of irritating proportions. While working on reinstalling windoze I managed to format the partition that ubuntu lived on. A side effect is the fstab is gone, and additionally the other partitions have lost any reference to what their files systems are. I tried using the live cd to see if it would detect the partitions on installation. The installer partitioner thinks there is one unified disk without partitions. However, using a supergrub disk still shows the other partitions but identifies them as unknown. I have not done anything to remove the data from those partitions does anyone have a decent suggestion on how to reestablish the partitions to make then functional again so that I might reinstall Ubuntu without destroying all the files that were not yet backed up? This seems like it ought to be simple, but the solution has not been discovered, no pun intended.

---

### Post by renzokuken on 2008-01-18
have a look at the **Ubuntu Rescue Remix** CD (google it) very useful tool that i think has something for partition table problems

---

### Post by Smbrandes on 2008-01-18
Thank you renzokuken, 

  Rescubuntu has testdisk, which is sufficiently verbose to allow for fumbling around looking for the wayward partitions. Essentially you chose the correct harddrive, analyse, (which ought to reveal the original partition structure assuming the drive was not totally formated), then write(which replaces the partition table on the drive). Then you can resume whatever it is you were up to previously. This saved an enormous amount of extra work.

---

### Post by renzokuken on 2008-01-19
so you used this and it worked? 

i accidentally 1% reformatted my old harddrive and lost the partition. i used Photorec and  Foremost to "data carve" out some of my old files.

if testdisk worked i would be most interested to know

thanks

---

