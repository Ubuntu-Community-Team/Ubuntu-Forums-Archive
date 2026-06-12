---
title: "raidz ubuntu 12.04 (xbmcbuntu) silly problem! files not truly writing to filesystem"
date: 2012-12-09
forum: General Help
---

### Post by ayounggun on 2012-12-09
Hi all would really appreciate some help with this problem I have - it's probably something simple :(

I have 3 x 4 TB disks in a NAS that I want to group together and access as if they were one whole 'unit'.

I also have a 250GB disk containing the OS - this is full of films and tv shows currently.

I thought zfs sounded good so I created a raidz zpool, after installing with apt-get

*sudo zpool create store raidz /dev/sdb /dev/sdc /dev/sdd*

and set the mountpoint to /mnt/store

*sudo zfs set mountpoint=/mnt/store /store*

checked it was successful - I think it was

[I]sudo zfs list

NAME    USED  AVAIL  REFER  MOUNTPOINT
store   266K  7.16T   170K  /mnt/store[/I]

Then I wanted to move over a whole load of files from my home directory. I went to where the to-be-copied folder was and entered

[I]sudo cp -R * /mnt/store

cp: cannot create directory `/mnt/store/media': No space left on device[/I]


It seems like it's not copying over to the new filesystem I made (or thought I did). I've never really done this type of thing until a few days ago so may be running before I can walk...

is there something obvious that I'm doing wrong? is this not the right way to copy files across? :confused:

thanks for the help!

---

