---
title: "Mounting a second hard drive for documents, pictures, and music"
date: 2013-12-10
forum: General Help
---

### Post by ryansmailinglist on 2013-12-10
My primary hard drive is a solid state 120 GiB with the following partitions: 1 MiB Bios Boot, 20 GiB root, 32 GiB SWAP, 68 GiB /home.  I have a second hard drive that is 2 TiB that is mounted to /mnt/data currently.  However, I would like the documents, pictures, music, and videos links in my file folder to be directed to that drive.  Do I need to remount the drive as a /user/~ or is there a way to point those folders to this drive?

---

### Post by drmrgd on 2013-12-10
What I usually do is to create the directories on my mounted media, and then for convenience make symbolic links from those directories to /home.  So, in my example, I have an external drive mounted to /media/data.  The permissions should be set to my username so that I can access the data.  In that directory, I create a directory like 'MyPix' and make a symbolic link to that directory in /home:

```

$ sudo chown drmrgd:drmgd /media/data

$ mkdir /media/data/MyPix

$ ln -s /media/data/MyPix $HOME/MyPix

```

Now I can just directly store pictures on that external drive, and when I want to access the directory, I can quickly get there from /home as though the directory resides in /home.  Is that what you're looking to do?

---

### Post by oldfred on 2013-12-10
I do the same as drmrgd, except I use /mnt/data.
The only possible difference is the /media mounts will show in Nautilus, /mnt will not and you have to drill down to get to them directly. But all the folders are linked so I have no reason to see the mount in Nautilus.

If there are no duplicate names or you rename or backup & delete the existing folders with same names.

#from home so default location of link is in /home/$USER
# cannot have duplicate entries, so move current to temporary location, repeat for each folder you want to move.
mv Music oldMusic
# Music is then also the folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

the 'echo /mnt/data/*' just needs to be the path to your data folders. You can check just by running it
echo /mnt/data/*

---

### Post by Morbius1 on 2013-12-10
I have an irrational dislike for symbolic links so if you are looking for an alternative use bind.

Let's say you have a folder in the second partition labeled Music. To temporarily bind that directory to your Music directory you can run the following command:
```
sudo mount --bind /mnt/data/Music /home/morbius/Music
```
[COLOR=#0000cd]*Change morbius to your own user name.*[/COLOR]

/home/morbius/Music now displays the contents of /mnt/data/Music. To restore things to where they were unmount it:
```
sudo umount /home/morbius/Music.
```

_To have this happen at every boot you can do it the easy way:_ Place that line without sudo in /etc/rc.local - above the "exit 0" line:
```
mount --bind /mnt/data/Music /home/morbius/Music
exit 0
```

_ Or you can do it my way :)_

I set up my own Upstart job: 
```
gksu gedit /etc/init/home-bind.conf
```
With this content:
```
# Remount partitions with bind
#
description "Bind Data Partition Subdirectories to My Home Directory"

start on stopped mountall

script
mount --bind /mnt/data/Music /home/morbius/Music
mount --bind /mnt/data/Downloads /home/morbius/Downloads
mount --bind /mnt/data/Movies /home/morbius/Movies
end script
```
Then I run the following command to execute it and make sure it works:
```
sudo initctl start home-bind
```

This method insures that the bind only happens after the /mnt/data partition is mounted first.

Symbolic links are easier to set up I just never liked them.

---

