---
title: "[SOLVED] Ok I's stumped with /etc/fstab, mtab, etc..."
date: 2008-07-04
forum: General Help
---

### Post by rp3 on 2008-07-04
Ok here is what I have.

8.04
LinkStation that has two mount points.

//linkstation/music
//linkstation/pictures

I can read and write to pictures but last week, something changed to where I can't write to the music mount?

Here is fstab
```
#//linkstation/music /mnt/linkmusic cifs username=rp,password=xxx,iocharset=utf8,file_mode=0777,dir_mode=0777		0	0
//linkstation/music /mnt/linkmusic cifs user=rp,pass=xxx	0	0
//linkstation/pictures /mnt/linkpics cifs username=rp,password=xxx,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0

```

Ok this is the mount point (ls -al)
```
drwxrwxrwx  8 root root    0 2008-03-30 10:51 linkmusic
drwxrwxrwx 14 root root    0 2008-07-04 22:20 linkpics
```

when I view a file in linkpics I see I don't own it but can read and write to it.  When I try in linkmusic I can only read?  I am stumped, as you can see I have been playing with the fstab file.. I have also played with chown to no avail either.  Setting myself as the owner changed nothing?

What baffles me is the ability in the one folder to write and the other not to be able to when I don't think I have changed anything?  It just stopped working it seems...  And this is common on other machines that have the same mount point.  Yes I tried to re-start the linkstation to no avail and also verified the setup of both points are the same on the linkstation...  Dunno..

Makes me think it isn't something on the Ubuntu Box but not sure.  Is there anything I am missing?

When I look at the directories in Nautlitus LinkPics shows with out the lokcs on each folder while music does.  I can right click in LinkPics and create a directory, and in Music I get this error.
```
Error while creating directory untitled folder.
There was an error creating the directory in /home/rp/linkmusic.
```

Oh and something I have always wondered about, what do the 8 and 14 mean in the ls -al??  

Thanks in advance, I am going to try to create a new mount point and see what it does while await your observations :)...

---

### Post by VMC on 2008-07-05
> **rp3 said:**
> Ok here is what I have.

8.04
LinkStation that has two mount points.

//linkstation/music
//linkstation/pictures

I can read and write to pictures but last week, something changed to where I can't write to the music mount?

Here is fstab
```
#//linkstation/music /mnt/linkmusic cifs username=rp,password=xxx,iocharset=utf8,file_mode=0777,dir_mode=0777		0	0
//linkstation/music /mnt/linkmusic cifs user=rp,pass=xxx	0	0
//linkstation/pictures /mnt/linkpics cifs username=rp,password=xxx,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0

```

Ok this is the mount point (ls -al)
```
drwxrwxrwx  8 root root    0 2008-03-30 10:51 linkmusic
drwxrwxrwx 14 root root    0 2008-07-04 22:20 linkpics
```

when I view a file in linkpics I see I don't own it but can read and write to it.  When I try in linkmusic I can only read?  I am stumped, as you can see I have been playing with the fstab file.. I have also played with chown to no avail either.  Setting myself as the owner changed nothing?

What baffles me is the ability in the one folder to write and the other not to be able to when I don't think I have changed anything?  It just stopped working it seems...  And this is common on other machines that have the same mount point.  Yes I tried to re-start the linkstation to no avail and also verified the setup of both points are the same on the linkstation...  Dunno..

Makes me think it isn't something on the Ubuntu Box but not sure.  Is there anything I am missing?

When I look at the directories in Nautlitus LinkPics shows with out the lokcs on each folder while music does.  I can right click in LinkPics and create a directory, and in Music I get this error.
```
Error while creating directory untitled folder.
There was an error creating the directory in /home/rp/linkmusic.
```

Oh and something I have always wondered about, what do the 8 and 14 mean in the ls -al??  

Thanks in advance, I am going to try to create a new mount point and see what it does while await your observations :)...

8 and/ 16 refer to the number of links.

On your first question, I've never seen that type of mounting before.

---

### Post by rp3 on 2008-07-05
> **VMC said:**
> 8 and/ 16 refer to the number of links.

On your first question, I've never seen that type of mounting before.


Ahh that makes sense, just never knew that, well I created a new mount point on the Linkstation and it behaves as it should (meaning I can write to it?)  I guess i will just move things and be done with it???

Bummer, just curious as it doesn't make any sense why something all the sudden doesn't work :)...

Baffling to me...

Oh well...

---

### Post by rp3 on 2008-07-05
> **rp3 said:**
> Ok here is what I have.

8.04
LinkStation that has two mount points.

//linkstation/music
//linkstation/pictures


Bla bla bla


Marked as solved as i have figured a work around, the original problem still persists...

---

### Post by VMC on 2008-07-06
> **rp3 said:**
> Marked as solved as i have figured a work around, the original problem still persists...

Could you post your work around. It might help someone in the future with similar issues. Also, it may give rise to another solution.

---

