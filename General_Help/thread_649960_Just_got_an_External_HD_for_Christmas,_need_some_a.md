---
title: "Just got an External HD for Christmas, need some advise..."
date: 2007-12-25
forum: General Help
---

### Post by thenetduck on 2007-12-25
I just got a new mini exteral hd for christmas (very happy) and I would like to be able to back up my system on it. 

It's formated as vFAT currently but I heard you can only create files 4gb in size on FAT ? What file system should I use to have a good backup but also allow me to use it on an apple,windows and linux machine? 

Thanks

The Net Duck

---

### Post by LaRoza on 2007-12-25
> **thenetduck said:**
> I just got a new mini exteral hd for christmas (very happy) and I would like to be able to back up my system on it. 

It's formated as vFAT currently but I heard you can only create files 4gb in size on FAT ? What file system should I use to have a good backup but also allow me to use it on an apple,windows and linux machine? 

Thanks

The Net Duck

FAT32 has a limit of 4 GB - 1 byte files.

You have an interesting requirement there. You are going to back your system up, why does it need to be used on three different OS's? If you are triple booting them, use Clonezilla to image the drive and format the external as EXT2 or EXT3, as only Clonezilla would need to read and write from it.

If it is large enough, you can create partitions on it.

What do you plan on using it for specifically?

---

### Post by thenetduck on 2007-12-25
Well here is he situaltion. ....

I have 1 160gb External that you plug in. and a new 160bg mini externial with no plugin to power required. I would like to keep a back up of all my media files on my mini with the ability to make it poratable. (file transfer etc) The old 160g gb hard drive I would like to be a basic backup hard drive that will only really need to be read by Ubuntu. 

I just wanted to be ableto have a 6 gb dvd or something on my mini external without it wigging out on me but still be able to use it with mac,windows and linux. 

The Net Duck
 Thanks

---

### Post by LaRoza on 2007-12-25
> **thenetduck said:**
> Well here is he situaltion. ....

I have 1 160gb External that you plug in. and a new 160bg mini externial with no plugin to power required. I would like to keep a back up of all my media files on my mini with the ability to make it poratable. (file transfer etc) The old 160g gb hard drive I would like to be a basic backup hard drive that will only really need to be read by Ubuntu. 

I just wanted to be ableto have a 6 gb dvd or something on my mini external without it wigging out on me but still be able to use it with mac,windows and linux. 

The Net Duck
 Thanks

Life is never simple.

I know nothing about Macs (except I can't afford them, although I want one).

With Ubuntu and Windows, NTFS is the best option. 

[http://www.macosxhints.com/article.php?story=20050521110452194&lsrc=osxh](http://www.macosxhints.com/article.php?story=20050521110452194&lsrc=osxh)

I guess NTFS is the best option for you.

---

### Post by motoperpetuo on 2007-12-31
i've got a related question: i dual boot between ubuntu and windows xp on my laptop, and i use an external hd, formatted to ntfs, as a backup. ubuntu can write to it fine, although ubuntu can't write to the ntfs partition on my local drive where xp is installed, for some reason. anyone know why? is there something i need to set in fstab to make my local ntfs partition writeable?

i also don't know much about macs. i don't understand why so many linux people seem to like them, though. seems like it's going from the frying pan into the fire as far as freedom goes (although i guess not everyone comes to linux for freedom, like i did). there must be another thread about this somewhere.

---

### Post by logos34 on 2007-12-31
> **motoperpetuo said:**
> i've got a related question: i dual boot between ubuntu and windows xp on my laptop, and i use an external hd, formatted to ntfs, as a backup. ubuntu can write to it fine, although ubuntu can't write to the ntfs partition on my local drive where xp is installed, for some reason. anyone know why? is there something i need to set in fstab to make my local ntfs partition writeable?

Sounds like you just need to run the ntfs-config gui and enable write support on **internal** drive

[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

> i also don't know much about macs. i don't understand why so many linux people seem to like them, though. seems like it's going from the frying pan into the fire as far as freedom goes (although i guess not everyone comes to linux for freedom, like i did)

Yeah, I don't understand it either.  Apple is almost as bad as Microsoft--same monopolistic urge sans tthe actual market dominance (unless we consider DRM/Apple Music). I think it's all about some kind of 'aesthetic chic'...iPods, iPhones, MacBooks, iMacs--they've become fashion accessories for today's yuppy class.  I have to admit the newest iMac caught my fancy, but when you look at the price tag and specs, well, I could build a better computer for slightly less--one that's easily upgradable to boot. I'd rather build my own and run linux on it anyday.  Especially 'bun2.  I will never buy an iPod.  I am not an iSheep. (i.e. I use ogg vorbis and flac whenever possible, and avoid aac or proprietary codecs.  I don't care that rockbox or whatever can play ogg on ipod...I demand a dap that supports ogg)

---

### Post by tylerspaska on 2007-12-31
i have the same situation (use windows, linux, and os x on a regular basis)  with a 40gb drive out of my old laptop. i usually use fat32 because i don't transfer movie files on a regular basis, but sometimes i reformat to ntfs so that i can move big files around.

ntfs is probably your best option. you're right, fat32 can only write up to 4gb. i think it actually stops at 3.99gb. Windows and Ubuntu have no problems at all with ntfs read-write. OS X can read ntfs but cannot write, although i've heard you can get it to work somehow...

i guess under ideal conditions i would format most of the drive as fat and then make an ntfs partition big enough for the movie files (or whatever else) i anticipate wanting to move around.

---

### Post by motoperpetuo on 2007-12-31
> **logos34 said:**
> Sounds like you just need to run the ntfs-config gui and enable write support on **internal** drive

[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)



Yeah, I don't understand it either.  Apple is almost as bad as Microsoft--same monopolistic urge sans tthe actual market dominance (unless we consider DRM/Apple Music). I think it's all about some kind of 'aesthetic chic'...iPods, iPhones, MacBooks, iMacs--they've become fashion accessories for today's yuppy class.  I have to admit the newest iMac caught my fancy, but when you look at the price tag and specs, well, I could build a better computer for slightly less--one that's easily upgradable to boot. I'd rather build my own and run linux on it anyday.  Especially 'bun2.  I will never buy an iPod.  I am not an iSheep. (i.e. I use ogg vorbis and flac whenever possible, and avoid aac or proprietary codecs.  I don't care that rockbox or whatever can play ogg on ipod...I demand a dap that supports ogg)

as much as i dislike apple, i must come clean and admit that i'm an ipod user. i just think the ipod is the best product on the market, or at least it was, for what i needed when i bought mine. i've got an 8gb gen2 nano, and it's perfect for working out, which is what i mainly do with it. when i bought it last year, i wasn't aware of any other player that size, with no moving parts (hence, able to handle getting bounced around during a workout), and able to hold 8gb of music. 

the new nanos are pretty squat and ugly, though. they don't look like they would fit in my pocket comfortably like my gen2. i know they do video, but who wants to watch videos on a 2" screen? hopefully by the time i need to buy a new player some of the ipods competitors will have caught up.

thanks for the advice on the ntfs problem, btw. i'll try that out.

---

### Post by logos34 on 2007-12-31
> **motoperpetuo said:**
> as much as i dislike apple, i must come clean and admit that i'm an ipod user. i just think the ipod is the best product on the market, or at least it was, for what i needed when i bought mine. i've got an 8gb gen2 nano, and it's perfect for working out, which is what i mainly do with it. when i bought it last year, i wasn't aware of any other player that size, with no moving parts (hence, able to handle getting bounced around during a workout), and able to hold 8gb of music. 

the new nanos are pretty squat and ugly, though. they don't look like they would fit in my pocket comfortably like my gen2. i know they do video, but who wants to watch videos on a 2" screen? hopefully by the time i need to buy a new player some of the ipods competitors will have caught up.

thanks for the advice on the ntfs problem, btw. i'll try that out.

Sounds like you did your homework before buying one based on your very demanding usage, but most people get one just because they're trendy, and their friends have one, you know.  It's a status symbol.  I'm not denying that iPods are innovative products, I just don't like the company, and I think for a lot of people there are other players perfectly capable of satisfying their needs.  iRiver and Cowan have some really good stuff IMO.  Apple is not the center of the tech universe.  Anyway, enough of that and good luck with the ntfs.

---

### Post by motoperpetuo on 2008-01-27
i just figured out how to do thanks on the forum, so i'm going back to give credit where credit is due. the ntfs suggestion worked perfectly, so thanks indeed.

---

