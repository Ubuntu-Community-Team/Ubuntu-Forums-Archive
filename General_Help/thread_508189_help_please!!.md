---
title: "help please!!"
date: 2007-07-23
forum: General Help
---

### Post by dragonwings on 2007-07-23
Im Going Crazy Here Im On Dail Up 56k .

Can Anyone Tell Me If It Is Possible To Make A Copy Of My Hard Drive Put It On To A Disk That Is Able To Intsall To My Hard Drive.

Iv  Tried  Aptoncd  But It Could Not Find Files To Copy Other Than Its Own Aptoncd File

Also I Tried Remastersys Which Found All My Files Games  Etc....
Which I Made A Live Cd From Which Worked Perfect As A Live Cd
But When I Installed It To Hard Drive And Tryed To Boot It Came Up With Grub 
Then Error 23 Or 22 Somthing Like That .

---

### Post by AceofSpades19 on 2007-07-24
The Constant Capital Letters Are Really Annoying And Make Your Post Hard To Read
you could use the dd command to copy your harddrive to a different, bigger disk, I haven't really used it so I can't really tell you what to type

---

### Post by kuja on 2007-07-24
Have you tried using something like partimage? It might work. After restoring the partition saved with partimage (assuming this image is small enough to fit on cd), you'll probably need to use the live/install cd to run the "grub-install" command to install grub.

Alternatively, assuming all you want is the same packages, you could just do this to restore all the packages you had installed in a new installation.
To make the list :
```
echo "sudo apt-get install $(dpkg --list | grep 'ii  ' | cut -f3 -d' ' | tr '\n' ' ') > installpackages.sh)" > installpackages.sh
```
To install the packages
```
sudo sh installpackages.sh
```

PS: The initcaps is kind of annoying.

---

### Post by dragonwings on 2007-07-24
Partimage sounds good ill give it a go .
do you know if there is any size limit gb wise
as my setup which i want to copy is 8.3gb.

---

### Post by aum11 on 2007-07-24
Clonezilla is also an excellent option for copying whole disks or partitions.

---

