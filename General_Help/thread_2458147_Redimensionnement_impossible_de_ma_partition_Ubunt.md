---
title: "Redimensionnement impossible de ma partition Ubuntu"
date: 2021-02-17
forum: General Help
---

### Post by dunivixs on 2021-02-17
Bonjour, 

J'ai essayé d'installer un jeu avec lutris mais celui ci est trop gros pour ma partition Ubuntu qui fait 107 Go (Il me reste 30 Go et il me faut 38 Go)
Il faut donc je trouve de la place quelque part, donc j'ai vidé ma partition Windows 7 et j'ai du coup une partition non alouée de 80 Go.
Sauf que je ne peux pas modifier la taille de ma partition Ubuntu car celle-ci est en utilisation donc j'ai booté avec mon PC sur GParted LiveUSB
mais je ne pouvais pas étendre ma partition (je pouvais seulement étendre celle de Windows 7).

Voici une image qui vous permettra de mieux comprendre mon problème : (oui je sais c'est le bordel)
[https://cdn.discordapp.com/attachments/434408303817261056/811637575328202816/Capture_decran_de_2021-02-17_17-36-40.png](https://cdn.discordapp.com/attachments/434408303817261056/811637575328202816/Capture_decran_de_2021-02-17_17-36-40.png)
(La partition que veux étendre est celle surlignée en orange et c'est /dev/sda6 et j'ai pris de l'espace depuis la partition /dev/sda2)

Merci de votre aide

---

### Post by Hagar Delest on 2021-02-17
Writing in French in an English forum limits the chances of getting a reply.

I would move the partition 4 next to the partition 2 (keeping the same size) and then resize the partition 3 to the left.

---

### Post by dunivixs on 2021-02-17
Ok I will add a new thread, but I don't really understand what you said

---

### Post by oldfred on 2021-02-17
If Google translate or if your understanding of English is poor, you can use the French Forum.

French Forums
[http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/)
 [www.ubuntu-fr.org](www.ubuntu-fr.org)

---

### Post by Hagar Delest on 2021-02-17
I've corrected my post. The partition 4 is to be moved next to the partition 2 (and not the 4 of course). Then it will free space left of the partition 3. Increase that one and you can increase the partition 6 as well.

There was no need of an additional thread, you could have merely rewritten your initial post.

---

### Post by oldfred on 2021-02-17
You are using the old MBR(msdos) partitioning.
That has the 4 primary partition limit and then one primary can be the extended partition to "hold" the logical partitions (your sda3).
All partitions from sda5 and up are inside the extended partition.

All logical partitions must be inside the extended partition, so the primary sda4 is between the extended and the un-allocated.

---

### Post by grahammechanical on 2021-02-17
Following on from what was said above. I suggest that you move partition 4 to the left so that the available space (espace disponible) is in front of partition 3 (partition entendue). Then expand partition 3 into the available space (82GB). That will put 82Gb available space inside partition 3. Now, you can expand partition 6 (Ubuntu partition) to take up the available space that is inside partition 3.

You do this from GParted in a Ubuntu live session

Regards (cordialiment)

---

### Post by dunivixs on 2021-02-18
If I have understood everything :
I will try to move the partition 4 on the left next to the 2.
Could I move it from Ubuntu with Gparted ?
And then I will expand partition 3 then partition 6 with Gparted LIVE USB.
On Friday I will say you if that has worked.
Thanks

---

### Post by Hagar Delest on 2021-02-18
I understand that your Ubuntu system is on the partition to be moved. If so, you have to do all the operations from a live USB key. Partitions that are mounted cannot be changed if they hold the system from wich GParted is running.
You could do that from the main system if the partitions to be rearranged had been for data not needed by the system.

---

