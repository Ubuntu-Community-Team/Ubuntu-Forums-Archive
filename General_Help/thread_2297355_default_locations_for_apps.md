---
title: "default locations for apps"
date: 2015-10-03
forum: General Help
---

### Post by matt18 on 2015-10-03
Ello all. I have an interesting question. I know in ubuntu it is somewhat hardcoded where apps are installed, but where is that location and how do you find out where it is going to be installed via software center?

Second question. In windows, i install all apps on seperate drive or partition for security reasons and because i like it that way. Here is my issue, i have ubuntu installed and i am runnimg out of hdd space, if i add a second storage drive, how do i utilize that space for more apps to install to? The first drive i installed ubuntu is pretty small and at that time i was under the impression i could pick install path haha. I dont want to be complicated. Just want to add a second hdd and be able to store pics, docs, and install apps to it in the most easiest way possible:)  

Thanks.

---

### Post by howefield on 2015-10-03
> **matt18 said:**
> Ello all. I have an interesting question. I know in ubuntu it is somewhat hardcoded where apps are installed, but where is that location and how do you find out where it is going to be installed via software center?

Don't think you will manage that with the Software centre but there are other methods, amongst which include..

1. Synaptic Package Manager (not installed by default) allows you to inspect the deb package properties including listing paths to where files will be installed.
2. [http://packages.ubuntu.com/](http://packages.ubuntu.com/) will give you a listing of all the files to be installed for any particular package.
3. From the command line, apt-file (not installed by default) will give you the information.

> Second question. In windows, i install all apps on seperate drive or partition for security reasons and because i like it that way. Here is my issue, i have ubuntu installed and i am runnimg out of hdd space, if i add a second storage drive, how do i utilize that space for more apps to install to? The first drive i installed ubuntu is pretty small and at that time i was under the impression i could pick install path haha. I dont want to be complicated. Just want to add a second hdd and be able to store pics, docs, and install apps to it in the most easiest way possible:)  

Yes, you can do that but it isn't so easy. There are threads in the forum that explain how if you search, eg [http://ubuntuforums.org/showthread.php?t=1617196&p=10098392&viewfull=1#post10098392](http://ubuntuforums.org/showthread.php?t=1617196&p=10098392&viewfull=1#post10098392).

---

### Post by grahammechanical on 2015-10-03
Storing documents, photos & other kinds of Data on a second hard disk is a good idea. I do that. It means that I can reinstall Ubuntu without the risk of loosing my data. It will free up space on the other disk and that may be enough. It all depends on the size of that first hard disk and the number and type of applications you want to install.

An alternative would be to install Ubuntu in a large partition on the new hard disk with another large partition for data and use the first hard disk for storing archived backups of your data.

Regards.

---

### Post by pqwoerituytrueiwoq on 2015-10-03
i think you would be better off moving other stuff to another drive for more efficient space usage, but it is the same process either way
system critical apps are in [FONT=courier new]/bin[/FONT]
special critical root use apps are in [FONT=courier new]/sbin[/FONT]
user apps are in [FONT=courier new]/usr/bin[/FONT] 
non critical root apps are in [FONT=courier new]/usr/sbin[/FONT]
manually installed stuff goes in [FONT=courier new]/usr/local/bin[/FONT] and [FONT=courier new]/usr/local/sbin[/FONT]


now for moving stuff around
1st decided how on the second hdd you wan it
do you want moved parts as there own partition or all in a single partition
use [gparted]("apt:gparted") to set it up how you like (i will assume you are going to use  ext4 partition)
note the **[COLOR=#ff0000]UUID[/COLOR]** (partition -> information)
if you want them all in the same partition we will need to **[COLOR=#ff0000]bind[/COLOR]** them
i believe it is best to use a live cd/usb from this point

lets assume you want a single partition for a folder
edit [FONT=courier new]/etc/fstab[/FONT] on the system (not the live session) and add this line
[FONT=courier new]UUID=9b0788c7-d6e9-4db2-84e1-53400beb745b /var/cache/apt/archives ext4    defaults        0       2[/FONT]
from this point the system will use the partition with a UUID of 9b0788c7-d6e9-4db2-84e1-53400beb745b as /var/cache/apt/archives
next we need to move the data to the new place
use the **[COLOR=#FF0000]file manager[/COLOR]** to open the [COLOR=#FF0000]**new partition**[/COLOR] and the [COLOR=#FF0000]**original one**[/COLOR]
open a [COLOR=#FF0000]**terminal**[/COLOR] and use [FONT=Courier New]sudo cp -av /media/ubuntu/system/var/cache/apt/archives /media/ubuntu/newPartation[/FONT]
now assuming you did that right you can delete the original stuff to free the space
[FONT=Courier New]sudo rm -r /media/ubuntu/system/var/cache/apt/archives/*[/FONT]

now lets say you wanted multiple folders on the same partition
make a partition for them
add a empty folder for each you want 
create a folder in [FONT=Courier New]/mnt[/FONT] where the partition will be mounted, eg [FONT=courier new]/mnt/expansion[/FONT]
now we need to add this to [FONT=Courier New]/etc/fstab[/FONT]
[FONT=courier new]UUID=9b0788c7-d6e9-4db2-84e1-53400beb745b /mnt/expansion ext4    defaults        0       2[/FONT]
now the partition will be mounted somewhere useful
now we are ready to [COLOR=#FF0000]**bind**[/COLOR] the folders with /etc/fstab
[FONT=Courier New]/mnt/expansion/folder                                /path/to/origin           bind    defaults,bind   0        0[/FONT]
now add the find line for each folder you want to move
then use [FONT=courier new]cp -av[/FONT] like i did above and you can then delete the original

i recommend booting the system before deleting the original files
* delete from live cd/usb if you do it from the install after binding or mounting you delete the new stuff as the old stuff is inaccessible but using space on the drive
you could delete it before moving it, but that is like deleting system32 while you are using it

---

### Post by matt18 on 2015-10-03
Ok, hmm. So my main ubuntu install is on a 40gb hdd. From what i have read, the beauty of linux apps is the ability to keep them super small and  that a full install with all the apps we can think of should fit on 30gb. So this leads me to the next step of moving my home folder to the larger sata1.5 drive. 

Hmm, just thought of something. Will i have to mount the larger drive to my "data" directory every time i boot up? The reason i ask... This is a family computer and i need it to be a simple setup. haha. Maybe i should buy an external usb case for it? Or is mounting the best?

Thank you all for your expert input:) my family and i are grateful. If you ever come to utah, ill cook you dinner. Im a pro cook. Hope you like smoked food and wood fired pizza haha. And i own a food trailer:)

Just found this. It helps a ton. Haha

 [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

One last question. Once the new drive is mounted, can i create shortcuts from lets say /home/docs and have it save yhe data to /mnt/media/data/docs folder or somehow "mount" docs, images, downlod folders on my large drive to the respective folders in /home. So to be clear, on my large drive, i have a folder named downloads and it is mounted to downloads in home filder. Then i have a folder named music on large hard drive that "mounts" to music in home folder and whenwvwr i save data to the music folder in home, it automatically saves it to the music folder in large drive. Thanks

---

### Post by howefield on 2015-10-04
> **matt18 said:**
> One last question. Once the new drive is mounted, can i create shortcuts from lets say /home/docs and have it save yhe data to /mnt/media/data/docs folder or somehow "mount" docs, images, downlod folders on my large drive to the respective folders in /home. So to be clear, on my large drive, i have a folder named downloads and it is mounted to downloads in home filder. Then i have a folder named music on large hard drive that "mounts" to music in home folder and whenwvwr i save data to the music folder in home, it automatically saves it to the music folder in large drive. Thanks

You could remove the /home/user/Documents folder, or if you have files inside it, copy over to the new drive then remove the original folder, then create a link to the new Documents folder on the larger drive with something like

```
ln -s /pathtonewDocumentsfolder ~/
```

Eg, For me , with my "larger" drive named Data mounted as /Data,  that looks like..

```
rm -r Documents Downloads Music Pictures Videos && ln -s /Data/Documents/ /Data/Downloads/ /Data/Music/ /Data/Pictures/ /Data/Videos/ /Data/Data_Store/.kde ~/
```

that removes the original Documents, Downloads, Music, Pictures, and Videos folders from my install and creates links to the ones on the larger drive (along with another one I use for kde applications). If successful, you end up with folder links with "shortcut" arrows indicating it is a link.

---

### Post by pqwoerituytrueiwoq on 2015-10-04
unless you go installing a lot of fancy games you would be fine with 16GB if all your personal files are on a separate drive
you can move your home folder just like described above with the archives folder

---

