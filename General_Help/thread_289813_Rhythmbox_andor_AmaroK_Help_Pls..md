---
title: "Rhythmbox and/or AmaroK Help Pls."
date: 2006-10-31
forum: General Help
---

### Post by dothedorky on 2006-10-31
Hello all.

I've just installed a bare bones version of ubuntu (had it a while back until windows crashed and then i just reformatted the drives leaving me with nothing) So no customizations (though I'm working on it). I'm working on the Breezy 5.10 Version. Alright enough background talk- onto my question.

I'm trying to import music from my itunes folder on my windows partition, however, i can't seem to even find a windows folder even when going through the parent tree directory. I partitioned the drives myself and I know windows still exists because it's all showing up perfectly on GRUB and loading time.

1) How do you import music from an itunes folder on a windows partition?
2) Rhythmbox or AmaroK? Which is better?
3) Is installing WINE absolutely necessary in getting my music files over to Ubuntu?

Thanks in advance guys.

---

### Post by Rumo on 2006-10-31
> **dothedorky said:**
> Hello all.
1) How do you import music from an itunes folder on a windows partition?

You have to make sure that your windows partition is mounted - that means that you can access it (it should be in a directory like /windows or /media/windows or whatever).

If it isn't mounted you have to add a line to your /etc/fstab file. Something like that:

/dev/hda1 /media/windows  ntfs defaults,nls=utf8,umask=007 0       1

/dev/hda1 is just a guess - it depends on your partition table. The directory /media/windows has to exist, of course (so you should create it, if it isn't already there). Note however that you won't have write-support for a ntfs-partition (it is possible though, but that's another story).

After that you can simply add the iTunes-directory to amarok's music collection. I assume that this is true for rhythmbox, too -  but i've never used it.

> 
2) Rhythmbox or AmaroK? Which is better?

This is really a matter of personal taste. I'm very pleased with amarok - but you will find a lot of rhythmbox-lovers, too. I don't really feel the need for a new music player, though - so i'll probably never learn about rhythmbox.

> 
3) Is installing WINE absolutely necessary in getting my music files over to Ubuntu?

No, it isn't necessary at all. It would be only necessary if you would like to use iTunes. In my opinion, amarok is far superior to iTunes though.

---

### Post by dothedorky on 2006-10-31
So what you're saying is i have to do a terminal "gedit"? Do i add those specific lines?

And yes, my windows ntfs partition is mounted on hda 1, but i also have a fat 32 which i created during partitioning because it kept telling me i didnt have enough room for linux (which i knew right upfront was untrue).

to directly import from itunes to AmaroK i'd need to make the windows partition visible? And if i dont have specific rights to make it this way, then how would i go about that?

thanks for the response and notice :)

Edit: as far as installing AmaroK how would i go about doing that?

---

### Post by Rumo on 2006-11-02
yes, you have to add this line. gedit will work. Just make sure you use sudo ('sudo gedit /etc/apt/sources.list') to make sure you have the necessary superuser-rights.

So, on which partition is your iTunes directory? Exactly this partition has to be mounted.

If your windows partition is mounted, it is visible and you should have access to it. You only have to know to which directory it is mounted. The command 'df' will tell you this.

Installing amarok is quite simple. Just type 'sudo apt-get install amarok'. This is it.

---

### Post by dothedorky on 2006-11-02
I'm not entirely sure which partition my itunes is on- wow i'm starting to sound like the uber-newbie... i suppose i should be heading my questions in a different thread haha.

i'm pretty sure its on the ntfs partition- however there might be some trace music files on the FAT32

Ever since I partitioned my drives, however, i noticed that some of my files in itunes are missing (tried to play them through in the party shuffle- not such a party if you catch my drift). I'm assuming that by creating a fat32 file partition, it split up the music files and distributed each music file evenly? 


Either way i have all the music i need on burned cdrw's... now all i have to do is find those haha.

Thanks for all your help again.

---

