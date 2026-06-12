---
title: "Removing Ubuntu with vista."
date: 2008-03-13
forum: General Help
---

### Post by MrUnth on 2008-03-13
I had a quick tryout and managed to create a partition with unbuntu on it, I had a look around and I think I will leave using ubuntu for when I know more about how to controll it. I had a look around and I know that deleting the partition with unbuntu will work, my only problem is I lack the vista CD (I didn't get one with my computer (Vista came with my machine instead of me upgrading it)) so I will need another way to repair the vista partition when the unbuntu partition has gone.

Any idea on which program to get to repair my vista partition when I begin this?

---

### Post by sandysandy on 2008-03-13
> **MrUnth said:**
> I had a quick tryout and managed to create a partition with unbuntu on it, I had a look around and I think I will leave using ubuntu for when I know more about how to controll it. I had a look around and I know that deleting the partition with unbuntu will work, my only problem is I lack the vista CD (I didn't get one with my computer (Vista came with my machine instead of me upgrading it)) so I will need another way to repair the vista partition when the unbuntu partition has gone.

Any idea on which program to get to repair my vista partition when I begin this?

have a look at the Super Grub Disk for repairing MBR.

i assume u are booting with GRUB. 

u can also consider leaving  ubuntu as it is also.

regards

---

### Post by MrUnth on 2008-03-13
> **sandysandy said:**
> have a look at the Super Grub Disk for repairing MBR.

i assume u are booting with GRUB. 

u can also consider leaving  ubuntu as it is also.

regards

I suppose I could leave the unbuntu partition, but I would at the least need to srhink it, I tried too make the amount of memory the two partitions have the same so I have 18 GB left on my vista partition, and I probably would end up sing that up.

---

### Post by sandysandy on 2008-03-13
> **MrUnth said:**
> I suppose I could leave the unbuntu partition, but I would at the least need to srhink it, I tried too make the amount of memory the two partitions have the same so I have 18 GB left on my vista partition, and I probably would end up sing that up.

try gparted live CD.

boot into gparted live CD and u can resize ur ubuntu partition. 

regards

---

### Post by LeoSolaris on 2008-03-13
Well...  you can go buy PartitionMagic or a similar product, or if you still have the Ubuntu install CD that you most likely used to install Ubuntu, if you go to the top panel, under System->Administration->Partition Editor. It case the ability to delete the partition Ubuntu made for itself, then re-expand the NTFS partition. (Don't forget to remove the SWAP partition, too)

We are sorry to see ya go, and we do hope that you come back soon. Till then, you may want to just use the LiveCD (the install CD) to get used to Ubuntu, since it doesn't install on the hard drive unless you tell it to, and it is nearlly fully functional, if a bit slow at times.

---

### Post by LeoSolaris on 2008-03-13
> **sandysandy said:**
> try gparted live CD.

boot into gparted live CD and u can resize ur ubuntu partition. 

regards

Teaches me to take a long time typing...   When I started there was nothing in this thread but his initial question.

Leo S.

---

### Post by MrUnth on 2008-03-13
I used Gparted and the super grub disk and managed to remove unbuntu without much effort.

Thanks for the advice, I'm liking the community already :)

---

### Post by sandysandy on 2008-03-13
> **MrUnth said:**
> I used Gparted and the super grub disk and managed to remove unbuntu without much effort.

Thanks for the advice, I'm liking the community already :)

Welcome:)

---

### Post by Mushed on 2008-03-13
Do NOT use Partition Magic, Acronis, or any other 3rd party software besides maybe gparted (i've never used it so i don't know) - Windows Vistas partition is very fussy. I've completely screwed up the windows partition twice now because of trying to use Partition Magic/Acrionis. The only thing that worked for me was the Vista disk management. Just type Disk Manager into the search in the start-button. 
-Not sure if using vista to my your linux partion would make ubuntu unbootable, but you said you wanted to remove it.

---

### Post by Mushed on 2008-03-13
> **sandysandy said:**
> Welcome:)
Oh... well. Nvm. =P

---

