---
title: "amarok remote mysql."
date: 2008-03-03
forum: General Help
---

### Post by nymusicman on 2008-03-03
I don't even know if this can be done. But here is the question anyway. I just bought a new Asus EEE PC and I noticed that it's primary media player happens to be amarok (awesome). However because of it's extremely small hard drive I really can't put much music on there. However I have amarok and mysql setup on my desktop and I was wondering if I could link the EEE pc over to my mysql database and have the music streamed over. Hence setup up amarok on the eee to say something like [http://192.168.1.100:3306](http://192.168.1.100:3306) (using a lan with router) and play the music out of the EEE from my computer. Possible?

---

### Post by kuja on 2008-03-03
Well, I'm not 100% with you on what you said, but I'll take a guess at it. Amarok doesn't require the music files to be local ..... they could be somewhere else on the network accessible by sftp/ftp/smbnfs .... etcetera thanks to the magic of KIOslaves.

ie: it could access something like "sftp://fred@comp1/home/fred/Music/blah.ogg" transparently.

You can have the collection DB on a seperate machine also, but I don't think that it will make more than a few MB of difference, so I don't think I would worry about that too much.

---

### Post by nymusicman on 2008-03-04
I'm sorry. I'm having a really hard time putting this into words. 


Here is the setup. Machine 1 contains amarok using mysql database to link to all the music stored on machine 1. Machine 2 wants access through amarok (located on machine 2) to the music on machine 1. To make this task easier I would like machine 2's collection to be built off of machine 1's mysql database (that amarok on machine 1 built). Assuming machine 2 amarok can use machine 1's mysql database I'm also going to assume that clicking on a song on machine 2 would automatically start streaming that song from machine 1.

---

### Post by PreviousN on 2008-03-04
Yes. It's certainly possible. I even do it for myself. Here's my setup:

Server (with RAID) has all my music. It also hosts my mysql database. It has the music mounted in /media/RAID. Server then builds amarok database of mysql. 

client mounts server using NFS in /media/RAID. Then, I tell it to connect to mysql database on the server. 

The difficulty is that music files need to be stored in ALL of the same places. But, I'm pretty sure you can use symbolic links, so that's good. Also, the versions of Amarok need to be the same because there are slight changes in their usage of mysql between them (according to developers). 

I'd recommend looking up "mysql Amarok" in google. Here's a link that I found by doing the same thing: [http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

---

### Post by nymusicman on 2008-03-15
That is a really good setup. But still not what I'm asking. Let's say just for instance that a media player was made that could run in windows, mac osx, linux, whatever and supported mysql databases. I'm asking if a mysql database can be used to stream the music over. Not mount a folder on another machine but just point the software at the database and stream the music. I don't want to mess with mounting because I have different ways of hooking the client up to the internet. I actually want to stream this stuff over the internet, not just my local area network.

---

### Post by Zack McCool on 2008-03-15
The database doesn't stream music.  It really has very little to do with the music at all.

The database stores the information about the music.  It stores the tags, the location of the cover jpgs, etc.  It stores the playlists.  The music is stored wherever you want.

You need your Eee PC to do the playing itself.  You do not, however, need that music, or the database, to be located on the local machine.  

On your Eee PC, mount the share location that has the Music.  Say /mnt/Music...   Now tell your local copy of Amarok where the music is, and where the database is (with proper credentials).  You'll also need the mysql database to be configured to allow for access from other machines (by default, it only allws connections from the localhost).  Now you can play your music on the Eee, with none of it actually being stored there...

---

### Post by nymusicman on 2008-06-01
Is there any way to use /mnt/Music as a Virtual office type situation so that no matter where I go as long as I can connect to the internet that folder can be mounted?

---

