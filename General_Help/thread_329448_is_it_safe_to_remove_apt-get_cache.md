---
title: "is it safe to remove apt-get cache?"
date: 2007-01-01
forum: General Help
---

### Post by fokuslee on 2007-01-01
Is it pretty safe to remove all the /var/cache/apt/archives. content? 
i only have 9 gig for ubuntu and im running out.  

also is there a good program to resize my partitions and convert ntfs to vfat? program can be  for windows or linux since im dual booting.

---

### Post by tribaal on 2007-01-01
By any means, yes.

The cache's only purpose is to avoid you downloading the same package twice should you install it twice (install - remove - install again). If you don't mind, just clear the cache with the "sudo apt-get clear" command.

- trib'

---

### Post by fokuslee on 2007-01-01
thank you for your timely response :D 

any ideas for my second question? i would like to convert one of my ntfs partition to vfat without loosing the contents on it.  

all suggestions welcome

---

### Post by raul_ on 2007-01-01
Impossible without a backup..maybe some member of the forum knows more than i do, but don't get too excited..it's easier to backup, format, and then copy your files again

you can resize partitions with Gparted. Since the partitions need to me unmounted, maybe you should run Gparted from the ubuntu Live CD, if you're planning on resizing the Ubuntu partition.
It's under System->Administration->Gnome Partition Manager

---

### Post by Sef on 2007-01-01
> any ideas for my second question? i would like to convert one of my ntfs partition to vfat without loosing the contents on it.


If you are going to convert one of your NTFS partitions, then you will lose the data on it.   What to do is to back up the data on that partition, then I would use [Gparted]("http://gparted.sourceforge.net") to change that partition to FAT32 or ext2 or ext3. And last, put the data back on the newly formatted partition.

---

### Post by fokuslee on 2007-01-01
my ntfs partition is not mounted by default (maybe b/c i used the alternative install cd?) and i never added it in fstab so im pretty much good to go with gpart.  
ntfs to vfat will loose all the data that sucks.  That partition has all my dls and also boot.ini for windows. (100gig plus of data) 

The alternative install cd feature something like resize windows partition before installing ubuntu i wonder if that can help my low ext3 disk space problem maybe i can still some space from winxp.  

Lesson learned here PLAN ahead before hastily installing OS (s)   
Again Thanks for all your help and Happy New Years!!!

---

### Post by raul_ on 2007-01-01
Why don't you tell us what your plans were? Allocating more space for ubuntu? Making the Windows drive available in Linux? Or none of my business? :rolleyes:

---

### Post by fokuslee on 2007-01-03
well its like this 
i want more space for ubuntu like 10 gig more 
cuz im using it more and more now
i want a shared partition with winxp
for all the dls (movies music programs)
The partition for dl is like 100 gig big and was made with winxp in mind only.  So ofcourse its ntfs
now i wanna change it vfat for obvious reasons.  

But obviously its not gonna work out until i get a big removable harddisk to dump all my current dl into b/c of the posts above

---

