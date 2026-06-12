---
title: "after using kleansweep ubuntu won't boot"
date: 2007-02-17
forum: General Help
---

### Post by disembodied on 2007-02-17
Hello,

I downloaded KleanSweep in order to clean up after a bunch of installs and uninstalls and what not. Anyway, I just cleared stuff I thought would be okay to clear but after clearing it all and restarting the computer ubuntu will no longer boot (windows boots fine). It gets to the ubuntu load screen (with the scrolling load bar) and has a little bit of the load bar showing but won't go any further.

Before actually commiting to the kleansweep actions I had it make a backup of all the files it altered/deleted... so I know I need to just untar the backup, but I do not know how to access my filesystem - I have the live CD but I don't know how to use it to get into my ubuntu file system on my harddrive.

If someone could explain to me how to do that (I searched and searched, I figure I may have just been using bad search terms because someone had to have had this problem before) I would really appreciate it.

Thanks,
Marcus

---

### Post by disembodied on 2007-02-17
*UPDATE*

I found directions on mounting a filesystem in recovery mode and attempted to follow them:
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu

but when i run mkdir it tells me it is unable to do that action because it is a 'read only filesystem'.

Also, if anyone can figure out how I can mount the filesystem I would also like to know what commands I need to run in order to find the specific filename (I know what directory it is in, but the filename had some generated numbers) - so basically a list contents of directory command... 

Thanks

---

### Post by disembodied on 2007-02-17
^--bump 

Man posts move back on pages quick...

---

### Post by disembodied on 2007-02-17
okay so i managed to use the liveCD and mount the filesystem and my home partition (its on a seperate partition but contains the kleansweep backup file) and I can open the backup file but when i go to extract it I am told I do not have permission - also the tar file is opened up as 'read only'... how do I mount the partitions and give my liveCD root write permissions? I know how to do this with windows partitions by editing a file, but how can I do it from the terminal since there are no files to edit and what not.

Thanks

---

### Post by disembodied on 2007-02-18
UPDATE - I fixed the situation...

Load up the live CD, mount the correct partitions, open up nautilus as the superuser (gksudo nautilus) navigate to the folder the drive is mounted under and right click, properties, permissions and change the 'other' permissions to be able to do everything, and click 'apply to all files/folders under'... that made it possible to untar the backup into the location and got ubuntu up and running again.

---

