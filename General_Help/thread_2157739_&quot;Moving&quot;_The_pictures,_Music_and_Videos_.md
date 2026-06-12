---
title: "&quot;Moving&quot; The pictures, Music and Videos folders"
date: 2013-06-26
forum: General Help
---

### Post by Extol11 on 2013-06-26
So I have windows setup so that the pictures, music and vieos folders are not in windows but in a separate storage partition. I suppose I can do the very same thing with lubuntu and I wanted to know how. I would like to just click the music folder and be taken to the same music folder that windows use that is not inside lubuntu's partition either. That way I can save space for steam games installations and just use my hard drive space better and have a more practical use of my OS. If anyone can tell me how to share folders like this, I'll be grateful.

---

### Post by dino99 on 2013-06-26
one of the many howtos around when googling: [http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7](http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7)

---

### Post by ajgreeny on 2013-06-26
I think dino99's link is more for sharing over a network and I believe you are just talking about the one machine with both OSs on it.

If I'm right you just need a separate ntfs partition for all your data which can then be read and written to by both ubuntu and windows.  You will need to make sure the ntfs partition is mounted at boot in Ubuntu by editing fstab, and you will most easily use the partition by linking the Music, Video, etc etc folders in the ntfs partition to folders in your /home of Ubuntu, so that when you click on the Music folder of Ubuntu you actually see all the files in Music on the ntfs partition.

It may sound fiddly and difficult but in fact is very easy to do, not only for windows and ubuntu dual boot systems but also for other linux and ubuntu dual boots, so if all this sounds too much for you, come back again for more help, giving us more detail of your current partition setup, etc etc.

See [https://help.ubuntu.com/community/DiskSpace#Partition_for_sharing_data_with_Windows.2C_MacOS..._.28optional.29](https://help.ubuntu.com/community/DiskSpace#Partition_for_sharing_data_with_Windows.2C_MacOS..._.28optional.29) for some more info.

---

### Post by sandyd on 2013-06-26
> **Extol11 said:**
> So I have windows setup so that the pictures, music and vieos folders are not in windows but in a separate storage partition. I suppose I can do the very same thing with lubuntu and I wanted to know how. I would like to just click the music folder and be taken to the same music folder that windows use that is not inside lubuntu's partition either. That way I can save space for steam games installations and just use my hard drive space better and have a more practical use of my OS. If anyone can tell me how to share folders like this, I'll be grateful.

Essentially, what you are probably looking for is a symbolic link

Firstly, copy the documents to the seperate storage partition (if they aren't already). Make sure their owned by you.
Then, setup the partition to be mounted automatically via fstab (See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab))
Then, rename the document/music/picture folders.

Run the below, replacing [original folder] and [destinatin] with the correct full paths
```
ln -s [destination] [original folder]
```

---

### Post by Extol11 on 2013-06-27
That's exactly what I was talking about. I gotta run some errands atm but I'll give those a try and let you guys know how it went. Thanks a lot.

---

