---
title: "need to reset all file permissions"
date: 2008-03-20
forum: General Help
---

### Post by Ender305 on 2008-03-20
I got fed up with not being able to move files into certain directories so I decided to change all of the file permissions 
I typed ```
chmod -R 777 /*
``` into the root terminal, so now I have a computer which cant load the gui and that has no sudo priveledges.
The only way I can do anything is to log in as root in the recovery console.

Is my only hope reinstalling the OS or is there some way to reset all of the permissions

---

### Post by leroyc on 2008-03-20
This is a very wrong approach:)

Unfortunately, the permissions are set at the installation of the files.

If you do not have many modifications, I advise the reinstall.

Also, please note its not the permissions, but the ownership that might have stopped you from moving files one way or another:)

If you are running an older version of Ubuntu - here is a great chance to upgrade to Gutsy Gibon - 7.10

---

### Post by nick_h on 2008-03-20
Changing the permissions of all files like that is a very bad idea.

I suggest that you re-install.

Backup anything you need to keep especially your /home directory.
Make a backup any files modified in /etc.
If you want to save the packages you have installed then backup /var/cache/apt/archives and save your package list using:
```
dpkg --get-selections > file
```

---

### Post by alexforcefive on 2008-03-20
> **leroyc said:**
> If you are running an older version of Ubuntu - here is a great chance to upgrade to Gutsy Gibon - 7.10

Hahaha! The eternal optimist! :D

---

### Post by Ender305 on 2008-03-20
ok, when I copy the home directory, should I do anything special to the permissions or owner, and can I just replace the new home folder with the old one, as long as the usernames are the same

---

### Post by forrestcupp on 2008-03-20
Wow!

> **Ender305 said:**
> ok, when I copy the home directory, should I do anything special to the permissions or owner, and can I just replace the new home folder with the old one, as long as the usernames are the same
It should work as long as you didn't screw up the ownership there.  It's worth a try, though.  What do you have to lose?

Next time you should ask the forum *before* doing something so drastic.

---

### Post by nick_h on 2008-03-20
By default, files in your home directory will be owned by <username> and in group <username> with permissions of -rw-r--r--

---

### Post by |{urse on 2008-03-20
> **Ender305 said:**
> I got fed up with not being able to move files into certain directories so I decided to change all of the file permissions 
I typed ```
chmod -R 777 /*
``` into the root terminal, so now I have a computer which cant load the gui and that has no sudo priveledges.
The only way I can do anything is to log in as root in the recovery console.

Is my only hope reinstalling the OS or is there some way to reset all of the permissions

OMG! <that's a terrifying thing to do to your box>

---

### Post by Mustard on 2008-03-20
> **|{urse said:**
> OMG! <that's a terrifying thing to do to your box>

Agreed. :)

It's amazing how often it happens though.  Over the years, reading this forum, I've seen this same problem repeated so many times. I even did something similar myself when I first started using linux.  I must have destroyed my linux install about 4 times before someone suggested that i have a separate home partition to ease the pain of reinstalls.

---

### Post by bodhi.zazen on 2008-03-20
> **Ender305 said:**
> I got fed up with not being able to move files into certain directories so I decided to change all of the file permissions 
I typed ```
chmod -R 777 /*
``` into the root terminal, so now I have a computer which cant load the gui and that has no sudo priveledges.
The only way I can do anything is to log in as root in the recovery console.

Is my only hope reinstalling the OS or is there some way to reset all of the permissions

It *may* be possible to recover and reset ownership without re-installing, but the time it would take to do that would be much longer, even longer if you are new to linux.

Much much faster to re-install. Including a new /home. Save any data you might want to external media (usb / CD / DVD) are re-install.

---

### Post by Ender305 on 2008-03-21
I got it working again(I'm using a live cd) but it wont let me copy the old home directory, /home is empty, the first time I looked at it, my home folder showed up as a generic file, I clicked on it and I got a popup saying> couldn't display jules
the attempt to log in failed can I go into the recovery console and copy it onto a flash drive, or will I have the same problem with not being able to view it

---

### Post by forrestcupp on 2008-03-21
You're probably better off just copying your important data and files into your new /home directory, and not trying to copy the whole thing.

---

### Post by Ender305 on 2008-03-21
no, I'm saying it won't let me copy anything, I tried going into recovery mode, but when I tell it to copy, it just says something like "exclude xxxx"

---

### Post by Nathan_M on 2008-03-21
It has occurred to me that there should be a program to do this... you feed it a directory, and it recursively puts default permissions on everything inside it. Screwing up file permissions is quite common... less common on a system-wide scale, but this program would be useful for almost any case. Maybe I'll have a go!

It would need to be able to guess the correct permissions for packages, and it would also need to be able to run from a LiveCD, and understand that /media/xxx should be treated as / in that case. Don't wait for me though, Ender.

---

### Post by Ender305 on 2008-03-21
mkay, I've decided to reinstall linux to a new partition and figure out what to do with the old one later, I still can't do anything with the old files

---

### Post by forrestcupp on 2008-03-22
you should be able to just boot into a recovery mode and find your old /home directory.  Go to the directory that the old /home is in and type:
```
chown username home
```
Substitute your username.  If you're not in the recovery mode as root, you'll have to put a sudo on that.

---

