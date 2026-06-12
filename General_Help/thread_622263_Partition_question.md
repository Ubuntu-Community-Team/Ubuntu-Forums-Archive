---
title: "Partition question"
date: 2007-11-24
forum: General Help
---

### Post by mushroomcloudwarrior on 2007-11-24
Well, i have a 86 gig EXT3 partition..

I've realised that i can't make changes to it unless i go through root, click on media and then open the partition as root. Because of this, i'm unable to upload pictures or files onto google mail to send them as attachments too. Also, i can't even view the picture files unless i'm opening them as root.

I know very little of Linux and have managed to slowly get things working through a lot of reading off these forums.

What should i do to have a normal partition that i don't need to log in as root to edit.

---

### Post by benerivo on 2007-11-24
I think you should be able to change the folder permissions of the mount point. If you do ```
sudo nautilus
``` and navigate to the mount folder, you can right click on it and go to permissions. Then just set it to read/write for all users.

---

### Post by rsambuca on 2007-11-24
> **benerivo said:**
> I think you should be able to change the folder permissions of the mount point. If you do ```
sudo nautilus
``` and navigate to the mount folder, you can right click on it and go to permissions. Then just set it to read/write for all users.

Actually, the correct code in this case is 

**gksudo** nautilus

---

### Post by benerivo on 2007-11-24
> **rsambuca said:**
> Actually, the correct code in this case is 

**gksudo** nautilus

I have seen this mentioned before. What is the difference, as sudo and gksudo both seem to work the same?

---

### Post by kellemes on 2007-11-24
> **benerivo said:**
> I have seen this mentioned before. What is the difference, as sudo and gksudo both seem to work the same?

[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

---

### Post by rsambuca on 2007-11-24
To make a long story short, any time you require root privileges and a new window with a GUI opens, use gksudo.  If you are running a command just in a terminal, sudo is the way to go.  

Although in most cases you will be OK just using sudo, there are a few instances where you can bork your system with the incorrect usage.

---

### Post by mushroomcloudwarrior on 2007-11-24
```
nikhil@nikhil-laptop:~$ gksudo nautilus
nikhil@nikhil-laptop:~$

```

It doesn't do anything ???

```
nikhil@nikhil-laptop:~$ sudo nautilus
sudo: nautilus: command not found

```

this is strange

---

### Post by mushroomcloudwarrior on 2007-11-24
I should mention that i'm using Kubuntu gutsy 7,10?

---

### Post by benerivo on 2007-11-24
Try konqueror instead of nautilus.

---

### Post by rsambuca on 2007-11-24
> **mushroomcloudwarrior said:**
> I should mention that i'm using Kubuntu gutsy 7,10?

Then 

kdesu konqueror

---

### Post by mushroomcloudwarrior on 2007-11-24
```

nikhil@nikhil-laptop:~$ sudo konqueror
Error: "/var/tmp/kdecache-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nikhil" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-nikhil" is owned by uid 1000 instead of uid 0.

```

Could someone please explain this?

and do i need to restart for effects to take place?

This is what i've done..tell me if it's wrong?
[IMG]http://i36.photobucket.com/albums/e37/mushroomcloudwarrior/snapshot3.png[/IMG]

---

### Post by rsambuca on 2007-11-24
```
kdesu konqueror
```

---

### Post by mushroomcloudwarrior on 2007-11-24
anyone?

---

### Post by rsambuca on 2007-11-24
What happens when you input 'kdesu konqueror'?

---

### Post by mushroomcloudwarrior on 2007-11-24
konqueror opens (in root mode i assume)

Then i changed the permissions (shown in screenshot above)

But i don't think it's fixed anything..was just asking you if what i've done is right

---

### Post by rsambuca on 2007-11-24
You want to actually change the owner.  It still says Root is the Owner.  Try under the Advanced Permissions button.

---

### Post by kaiju on 2007-11-24
on the partitions i set to automount when i installed ubuntu, the permissions look like this:

owner: root (read & write)
group: plugdev (read & write)
others: (read only)

thought this might help :)

---

### Post by mushroomcloudwarrior on 2007-11-25
[IMG]http://i36.photobucket.com/albums/e37/mushroomcloudwarrior/snapshot4-1.png[/IMG]

that is what the advanced permissions look like..i can't figure out how to change the owner.

and Kaiju, your permissions are pretty similar to my permission snaphot provided above, isn't it?

---

### Post by kaiju on 2007-11-25
from what i could see on your previous screenshot, for your disk both owner and group are set to root. that is why i mentioned that for me, the group is set to plugdev.

however, the most simple solution would probably be to change the owner to your user. you can do this by opening up a terminal and tiping
```
sudo chown -R *your_username* /media/sda7
```
where chown is a program for changing file ownership and -R stands for it acting recursively.

---

### Post by mushroomcloudwarrior on 2007-11-26
That seems to have worked.

Thanks a million man :)

---

