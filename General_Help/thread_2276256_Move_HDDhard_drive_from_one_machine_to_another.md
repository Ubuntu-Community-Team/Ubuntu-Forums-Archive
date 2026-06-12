---
title: "Move HDD/hard drive from one machine to another"
date: 2015-05-01
forum: General Help
---

### Post by OBJ on 2015-05-01
Hello everybody. This is my first post here on the forums and being new to Ubuntu/Linux please take it easy on me ;)

So I currently have a 3TB HDD jammed packed (about 88% full) with movies/TV series/music in my rig. My folks also have a 3TB HDD in their machine.

I plan on installing Ubuntu on their computer also. I removed the 3TB HDD from their machine,wiped it, gparted it to ext4, and installed it alongside (plugged into MOBO SATA) 

mine so I could transfer files easily and somewhat faster then other methods (USB or network). To access their newly formatted ext4 drive, I needed to change the permissions

 from root to my user name. Used gksudo nautilus, and from the gui right clicked on the drive properties/permissions and set it to my user.

SO that is the what has been done so far. 


MY MAIN QUESTION is once I remove their 3TB HDD with all the files on it and with it set to my users permissions (from my machine) will I have any 

problems changing the user once the 3TB HDD has been moved into their machine. It takes a good amount of time to copy over 2.7TB (roughly) of data just want to make sure 

that once installed into their machine I can switch the read/write/delete/etc privileges to their user/machine and have no problems accessing the files at all.

Thank you guys for any help you can give

BTW not sure if it matters but using Ubuntu 14.04 LTS  on my machine and the same will be installed on my folks machine

---

### Post by Holger_Gehrke on 2015-05-01
Using a variation of the same procedure you used to take ownership of the drive should work for making them accessible on the other machine. Might not even be necessary, file and directory ownership is stored as a numerical user id (UID) and these are unique on one machine but repeat across machines, with the first user getting UID 1000 (lower UIDs are used for system users running server processes). So if you are the first user on your machine and your folks get the first user id on theirs, everything should be fine without any additional work. If it isn't, a quick 'sudo chown -R "username" "/path/to/mounted/drive" ' in a terminal will fix the ownerships.

---

### Post by oldfred on 2015-05-01
If doing a full install, are you setting your name or their name as the user & password?

Whenever I create a new data partition, I run these two commands, chown & chmod. But never run them on the system folders/partitions or else you will have to reinstall.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

Question.
I do not have a 3TB drive and you have to use gpt with that drive. For all my smaller drives I now only use gpt but have to set that first in gparted (device, advanced). Did gparted automatically use gpt when partitioning your drive?
sudo parted -l

---

### Post by OBJ on 2015-05-21
Just wanted to pop in and thank you both for the replies. Had no problems with the drive, the 3TB was in the machine prior to the Ubuntu install...but had no problems using it right off the bat. Just commented the UUID in fstab so it would be mounted upon login and all is well.

Thank you for taking the time to answer my question :)

---

