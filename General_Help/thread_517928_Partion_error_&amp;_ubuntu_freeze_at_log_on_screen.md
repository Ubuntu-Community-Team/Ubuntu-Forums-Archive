---
title: "Partion error &amp; ubuntu freeze at log on screen"
date: 2007-08-05
forum: General Help
---

### Post by jeyaganesh on 2007-08-05
Hi,
While installing ubuntu 7 , I got this error message during manual partioning step 'Files system does not have expected sizes for Windows to like it....'. It is also allowing me to do only 4 partions. Vista already occupied 3 partions and I couldnt make 'swap' partion. Eventhough I ignored the error message and installed ubuntu, but at 'log on' screen system got freeze.

With XP, I installed ubuntu 6  lot of times, I never experienced such a problem before. Please give me some solution to fix this problem. I too have problem with my 20" inch wide screen, but I found some solution from our forum. Next thing I have to make my belkin usb wireless adapter to work with ubuntu.

Please give me solution to fix the installaiton errors.


Jay:guitar:

My computer configuration is;
Dell Dimension E520, 20" Monitor, Intel Pentium VII V 2 cores 3 Ghz, 3000 Mhz
Intel integrated graphic card, 320 GB, 40 MB occupied by ESIA (Whats that?), 10GB for recovery CD and remaining is for C:/. Vista Home Premium.

---

### Post by randomnote1 on 2007-08-05
Vista is taking up 3 partitions?  That seems like to many.  Did you do the install or did it come like that straight from the factory?

If it came straight from the factory, check your partition types.  Make sure Vista isn't hogging 3 Primary Partitions.  If it is, you should be able to create a 4th Extended Partition.  In the Extended Partition you will be able to create your ext3 partition for your OS and a SWAP partition.  

Kind of a side note...I wonder if the first partition is really small...say under 500 MB to be used as a boot partition.  If that is the case, Vista may not have created it large enough to share with Grub.  Just a thought.

Anyway, good luck, and let us know how it goes!

---

### Post by jeyaganesh on 2007-08-05
Thanks for your suggestion, I will try it and inform here.
Jay

---

### Post by jeyaganesh on 2007-08-07
Hi tried lot of times with manual partion, i got the following error;
'Files system doesnt have expected sizes for Windows to like it. Cluster size is 2K (1K expected); number of clusters is 20017 (39957 expected); size of FATs is 79 sectors (157 expected)'. Could anyone tell me what should I do next? If I ignore and continue the installation, system freeze at 'log-on' screen. Is there any solution for me? Please.

Jay:guitar:

---

