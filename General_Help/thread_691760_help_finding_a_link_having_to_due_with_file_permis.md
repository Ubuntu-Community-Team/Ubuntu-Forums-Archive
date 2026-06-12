---
title: "help finding a link having to due with file permissions."
date: 2008-02-08
forum: General Help
---

### Post by -MoonDoggie- on 2008-02-08
i've already tried searching the forum for the link for like.........maybe 2-3 hours? anyway, i haven't had any luck so i'm hoping someone will know what i'm talking about and point me in the right direction.

the problem is i'm trying to give myself write access to one of my folders. its  partition on my hard drive that was ment to be a share point between windows and linux. the majority of my files would be kept here like music, games, downloaded programs, etc...but i forgot how to give myself write access to it. i had found a link that allowed my to write files to that drive without having to take the risk of doing it under "sudo nautilus". 

the best description that i can give of the link is that it guided me through a process which had me open nautilus in a weird way. (if that was even opening nautilus. the best i can remember of the command was that it was *something* nautilus) after typing the command another little window opened that kinda looked like the linux search indexer that you find on your top panel. what i did after that is kinda hazy but it eventually had me opening the properties of my share drive and giving myself permission to it.

the link had pictures as a guide as well. the best description i could give of it, sorry -_-.
thanks to whoever reads this mess and lends a helping hand.

---

### Post by taurus on 2008-02-08
What filesystem is that partition that you use to share stuff between Ubuntu and windows?  Is it ntfs?  If that's the case, you just want to mount it with ntfs-3g driver so you can write to it without root privilege.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by -MoonDoggie- on 2008-02-08
no no, i'm sorry. i should have been clearer. the problem isn't sharing between linux and windows. the problem is that i can't really save any files to the partition. files such as ones that i've downloaded from the net. 

the partition is a ext3 format. but i already know which driver to use to be able to access via windows. 

i guess one could say that i'm using this partition as a alternate /home directory that both windows and linux will be able to access without the fear of accidentally screwing up a system file.. the problem is just getting the permanent privilege to be able to write files to it. the link that i'm looking for does just that though. 

thanks again for any help that gets passed my way.

edit: forgot to mention that the majority of the files being written will be done from linux, as that is the OS i will be on most of the time.

---

### Post by taurus on 2008-02-08
If it's ext3, then why don't you change the ownership of that mount point from root to your login name so you can write to it anytime you want.  _Assuming_ the mount point is /media/share and your login name is **doggie**, do

```
sudo chown -R **doggie**:**doggie** /media/share
ls -la /media
```

---

### Post by -MoonDoggie- on 2008-02-09
.........to think that i wasted all that time, and developed quite a headache, being hell bent on finding a link who's end product was the exact same thing as this command i had seen a hundred times while searching the forums......thanks for saving me about another hour or so of searching tarus. +1000 karma points to you dude.

---

