---
title: "Unable to access encrypted drives mounted under another user..."
date: 2014-07-30
forum: General Help
---

### Post by nuts2 on 2014-07-30
I have two drives that are encrypted and mounted under my user name using the default built in encryption facility. I would like to give access to them for other users logging into the system via SSH/SFTP. Right now only my user account can access these drives over SSH and I have tried messing with the file system permissions but it still doesn't allow anyone but me to access them. Is there some type of mount options or something I can do so when the other users log in they can access these encrypted drives?

These drives mount under /media/user/ and that is default config. I have been searching for an answer to this for about a week now and haven't been able to figure out out. Any suggestions guys/gals?

---

### Post by ian-weisser on 2014-07-30
The whole point of encryption is that others cannot access your files.

Giving other people the key to decrypt your entire system seems unwise, and rather contrary to the purpose of using encryption.

If you want others to access some of your files, perhaps those files shouldn't be encrypted. Or perhaps they should be encrypted separately, with a different key that can be shared among the people you trust.

---

### Post by nuts2 on 2014-07-30
I just tried it with a drive that isn't encrypted and got the same result so I don't think it has anything to do with the encryption after all. The user that mounts the drives can access them no problem but other users logged into the system via SSH just get permission denied. I am going to guess it has something to do with the mount options but I don't know where to mess with those.

---

### Post by nuts2 on 2014-07-31
After doing more research and testing I am thinking more and more it has something to do with the mount options but I can't figure it out. I can't be the first one to run into this problem so perhaps someone else can help me out here. I want users who ssh into this system to be able to access the other drives and not just the primary drive.

---

### Post by nuts2 on 2014-07-31
I tried adding permissions to the drive to the group I assigned to my users but it didn't have any impact on the problem. Am I the first person on planet Earth to have an Ubuntu server with more than one drive in it?



[LIST]
[*=left]  sudo chgrp plugdev /media/mynewdrive
[FONT=inherit][/FONT]  sudo chmod g+w /media/mynewdrive
[FONT=inherit][/FONT]  sudo chmod +t /media/mynewdrive
[/LIST]

---

### Post by nuts2 on 2014-07-31
In the application Disks I can see there is an option to mount the drive at system boot and I am curious if that might be the answer to my problem. Has anyone tried using that option and if so what user does the drive mount under when that option is selected?

---

### Post by ian-weisser on 2014-07-31
> Am I the first person on planet Earth to have an Ubuntu server with more than one drive in it?
Not at all. I'm following with interest.

On my server, users don't get to mount anything. Root mounts most resources at boot, and access to each resource is permission-based.
My users get to mount one directory themselves (but they don't know it - their private backup drive mounts when they login).
So I lack experience with the concept of random users mounting/unmounting shared resources.

---

### Post by nuts2 on 2014-07-31
> **ian-weisser said:**
> Not at all. I'm following with interest.

On my server, users don't get to mount anything. Root mounts most resources at boot, and access to each resource is permission-based.
My users get to mount one directory themselves (but they don't know it - their private backup drive mounts when they login).
So I lack experience with the concept of random users mounting/unmounting shared resources.

What I am looking for is a completely encrypted system to prevent physical intrusion in case of theft. I have a few users that will need to access the system and the drives in it and I intend to control their access with file system permissions. I would like all drives unlocked and mounted at boot so it is transparent to the users that will SFTP into this system to backup and retrieve files. I am pretty knowledgeable with file system and user permissions but this appears to be a problem with the way I am mounting it and I don't know what I am doing wrong. Each time I log in I have to mount them and provide the password and they mount under /media/user/. I am pretty sure the drives being mounted by a user is the problem but that is as far as I can seem to get. I have access to a full lab environment so I have been testing and trying all kinds of things and I have reached a point where I have nothing left to try and need some help.

---

