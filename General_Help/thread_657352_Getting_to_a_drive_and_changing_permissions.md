---
title: "Getting to a drive and changing permissions"
date: 2008-01-03
forum: General Help
---

### Post by techgeek40 on 2008-01-03
I have a flash drive on my computer (1 gig) that I have put a folder of music on from my Vista computer
The problem is - the flash drive is reading the file as locked and I can't change permissions

How do I get to the flash drive (it's called My Sh!t --- lol sorry that's the drive name I gave it - so replace the ! with an I - ).

What I want to do is get to the flash drive - change the permissions so I can add/delete/rename the folder/files

Thanks

---

### Post by carrett on 2008-01-03
Well you could try changing the permissions using chmod and sudo:

```
sudo chmod -R <whatever permissions you want (man chmod)> "My ****"
```

Out of curiosity, though, do you have any other removable drives? Do permissions on them work OK? This could be a matter of configuring HAL or something.

---

### Post by techgeek40 on 2008-01-03
I'm a newbie - can you go a little further

I want read/write permissions on the Flash Drive - so I would??

sudo chmod +R ?????? (this is where I get lost)

---

### Post by carrett on 2008-01-03
```
man chmod
```

The -R bit I mentioned makes it recursive. For example, the following would make it read/write-able by all users (not very secure):

```
chmod -R a+rw <directory>
```

It's all documented very nicely though if you just read the manual page I mentioned. Explained much more completely than I will ever be able to do.

---

### Post by taurus on 2008-01-03
Is your flash drive ntfs or fat32?  Chances are it is fat32.  Can you post the output of this command from a terminal?

```
df -h
```

---

### Post by techgeek40 on 2008-01-03
Actually I can format the flash drive with my Vista machine.
But I have some files in My Music folder that have a lock on them - I can play the audio files - but I can't delete them

How do I take "ownership" of that folder?

If I'm in Terminal and do sudo su <then my password"
Then cd to my music's folder --- what would I type in terminal to allow me to have full access to it (delete/rename - whatever)?

---

