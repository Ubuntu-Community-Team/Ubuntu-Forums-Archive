---
title: "Moving Home on General Root Mounted Install?"
date: 2015-06-28
forum: General Help
---

### Post by Alebin on 2015-06-28
I installed Ubuntu 15.04 and set one partition's mounting point to / and left it at that, not creating any other partitions. I was wondering if I could make some room on another drive with gparted maybe and move my /home to that without ruining anything. I also didn't create a swap partition, and probably need to do the same thing for that, but I think that's just a matter of pointing it to a gparted created swap partition in /etc/fstab, right?

---

### Post by Bucky Ball on 2015-06-28
There is tons of info on moving your /home partition. Have a try of one of [these]("https://duckduckgo.com/?q=move+home+partition+ubuntu+14.") and let us know where/if you get stuck.

Note: Clone the partition or backup prior to commencing anything. You are going to need to boot from live media and 'Try Ubuntu' to adjust sizes on your / partition. Stick a 2Gb /swap at the end.

PS: An alternative is ...

Create a large data partition> create directories on there that match the directories in your /home directory in /> move the data from the corresponding directory in /home to the directory in /data. For instance. 

You have /home/user/Documents. Move all the data in /home/user/Documents to /media/data/Documents

Once you know you've securely stashed the info, delete the directories in the /home directory in / and replace them with symlinks to your data in /media/home/<directory>. Symlinks are easy. From [here]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html?showComment=1275427925979"):

> To create a symlink one uses the program ln. In a console window, navigate to the directory where you want to create a symlink directory and type the following:

ln -s 'location to link to' 'name of symlink'

For example:

ln -s /media/data/Documents /home/user/Documents

This will create a link call 'Documents', which will look and act like any regular directory, to the 'Documents' directory /media/user/Documents. With the free space from moving your data from / you can shrink your / partition. 

Just another option. :)

PS: Do not move hidden folders when you do this. That is the only difference with the alternative method I outline. If you move /home directory to another partition, you move all user settings with it (hidden directories and files). If you use symlinks, they stay on /.

---

### Post by Alebin on 2015-06-28
Thanks. I found this guide under partitioning: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Bucky Ball on 2015-06-28
Symlinks are a viable alternative. The only difference is in the PS of my last post which I just edited before I saw your last post.

Let us know how you go with it and if you run into any brick walls. Good luck and make sure you back up first ... :)

---

