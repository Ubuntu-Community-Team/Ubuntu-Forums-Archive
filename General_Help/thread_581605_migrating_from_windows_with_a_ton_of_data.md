---
title: "migrating from windows with a ton of data?"
date: 2007-10-19
forum: General Help
---

### Post by devliljohn on 2007-10-19
ok so i have a home server running XP that i use as mass storage for all my data, which happens to be about 400 GB of movies, songs, pictues, apps, videos. i have a total of 600 GB of drive space on 2 identical 300 GB maxtor sata drives. in an effort to force my self to lern more about linux servers i want to install ubuntu server on it. 

heres the issue, i want to keep all my data. i was thinking i could install ubuntu then slowly move my stuff over to a linux partion in stages, move data over from the ntfs to the linux file system and then shrink the ntfs and grow the linux partition and move more stuff over untill all my stuff is in linux and i can completely kill windows. but i am told that you can't resize ext3. is there a linux file system that can be resized? 

i guess i could just keep all my data on the ntfs since ubuntu can read and write to it now. but i would rather not do that becuase i don't want to have to worry about defragmenting the NTFS. 

any one got any suggestions?

---

### Post by steveneddy on 2007-10-19
I would buy an extra HD, remove one of the drives, install the new one, slip a live CD into the CD drive and format the new drive for ext3, cpoy everything from the old drive to the new Linux drive, repeat with the other drive, leaving a partition on one ov the drives large enough for the Linux OS of choice to be installed.

This would also give you another HD to store even more data/movies/music/Ubuntu screenshots.....

:popcorn:

---

### Post by strabes on 2007-10-19
> **devliljohn said:**
> i was thinking i could install ubuntu then slowly move my stuff over to a linux partion in stages, move data over from the ntfs to the linux file system and then shrink the ntfs and grow the linux partition and move more stuff over untill all my stuff is in linux and i can completely kill windows.

This would be really really dangerous and tedious. Your best option is to put all the data on a different drive, install ubuntu server on the drive where windows is right now, then plug the drive with the data into the server box. This way, you'll avoid having this same problem again if you ever have to reinstall ubuntu server. I wish you luck.

By the way, what OS is installed on most of the computers that are going to be accessing this data?

---

### Post by devliljohn on 2007-10-19
> **strabes said:**
> This would be really really dangerous and tedious. Your best option is to put all the data on a different drive, install ubuntu server on the drive where windows is right now, then plug the drive with the data into the server box. This way, you'll avoid having this same problem again if you ever have to reinstall ubuntu server. I wish you luck.

By the way, what OS is installed on most of the computers that are going to be accessing this data?

unfortunatly, Windows. 

i have about 20-30 form all over the world that access my server via FTP over TLS, which is being server by filezilla server. and i have 2 or 3 computers at home my Laptop which is Ubuntu/Windows, and my work laptop which is windows, and the family computer which is going to be ubuntu soon, that use Samba/windows share.

---

