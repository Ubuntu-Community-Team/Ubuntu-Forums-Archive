---
title: "Partitions and were to store you files?"
date: 2012-10-16
forum: General Help
---

### Post by MortenSJ on 2012-10-16
Hi

I am totally new to Ubuntu and have spend the last 3 days with reading, testing, playing around and i definitely see the opportunities in Ubuntu :)

I have a few questions i hope you guys can help me with. I have messed around with Ubuntu Server 12.04, and i hope you guys can help me a bit.

My system is like following. I have a 60GB SSD and a 2 TB storage. My plan is to run Ubuntu Server on the 60GB SSD and then have all my files on the 2TB HD.

When i install Ubuntu a home folder was created /home/username/ Is this were i would put all my files, movies, documents, images and so on?

I don't remember the installation, but is it possible to make the /home/username/ to be on my 2TB HD?

I have read that people also create partitions for /root, /swap. What is that and why do you do that?

What would be the best way to setup the system i described above? Would it be to have the /home/username/ on the seperate disk (2TB HD)?

I hope you guys and help me, cause i'm a little confused on the structure :)

Thanks in advance!

---

### Post by Bucky Ball on 2012-10-16
Yes, when installing if you choose 'Something Else' you can manual partition and put /home wherever you want. (and also adjust partition sizes). And yes, /home is where you put all your stuff.

If you don't want to reinstall, you could try this. Create a folder on the 2TB for the contents of your /home. Copy all the folders from /home into this folder. Once you know your stuff is safe, delete the folders in /home (excluding desktop and hidden folders which start with '.firefox' for instance. These are settings and shouldn't be visible folders anyway.

Now, create symlinks to the folders in the new folder on the 2tb in the original /home folder on / by this syntax:

```
ln -s <source> <target>
```For instance, you want to link the 2tb folder /Documents into the old /home folder:

```
ln -s /media/2tb/Mydata/Documents /home/username/Documents
```You would need to change details to match yours, naturally. ;)

PS: The 2Tb will need to be mounting at boot else you'll have to mount manually to access the folders symlinked to it in your original /home. Hope that all makes sense.

---

### Post by MortenSJ on 2012-10-16
Thanks for you answer! 

I managed to move my home folder by using this guide and it worked

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I have also installe sabnzbd and got it to work. Right now its downloading into /home/nas/downloads/complete

What i would like is to have it download into /home/nas/media/ but i can't change the folder path. Should i create symlinks like you just showed me?

Or should i keep everything inside /home/users?

---

### Post by MortenSJ on 2012-10-17
I'm just curious.

I always thought that the most logical thing was to seperate my user files with my storage. Correct me if i'm wrong :)

Since i have a 60GB SSD and a 2TB storage wouldn't it be more logical to just install Ubuntu and the /home/user folder on the 60GB SSD and then create a /media partion (my 2TB HD) were i would keep all my files?

---

### Post by oldfred on 2012-10-17
That is what I do. I want to have a fully bootable system on every drive, but data can be anywhere. So I keep /home inside my / (root) on my SSD, but have all my data in other partitions and other rotating drives. Then /home only has the hidden files & folders. I have not moved .wine as that is more difficult to move, but also moved Thunderbird & Firefox profiles as I use the same ones in multiple systems. 

Splitting home directory discussion and details - both linking & use bind:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by otetiani on 2012-10-17
Question on the symlink from Bucky Ball:  Is it possible to break the link with an update?

---

