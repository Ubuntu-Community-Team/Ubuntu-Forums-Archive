---
title: "Cannot Modify &quot;Permission&quot;"
date: 2007-08-20
forum: General Help
---

### Post by suhu_achonk on 2007-08-20
I have a partition (NTFS), has already mounted! I can read or write on it...
The problem is, inside this partition, there are a folder that i want to protect...

I have to try this step in order to protect the folder :
- Right click on the folder
- Properties
- Permission
There was nothing i can do here...because it says : this folder belonging to 'root'

So that, i log in as 'root' , and do the same way...
but..why i can not make a change to the permission...i always back to default setting...

or...can you help me...with another way ? 

thx

---

### Post by southernman on 2007-08-20
In a terminal do:

> sudo chown -R username:username /path/to/directory

replace username for your username and enter the correct path the the directory in question...

---

### Post by suhu_achonk on 2007-08-20
> **southernman said:**
> In a terminal do:



replace username for your username and enter the correct path the the directory in question...

sorry bro...i'm a newbie in linux...can you tell me more detail ? eg : my folder inside :
/media/sda5/songs
i want to protect the 'songs' folder...

thx

---

### Post by southernman on 2007-08-20
> **suhu_achonk said:**
> sorry bro...i'm a newbie in linux...can you tell me more detail ? eg : my folder inside :
/media/sda5/songs
i want to protect the 'songs' folder...

thx
We all were at some point... you'll get it in due time. ;)

To open a terminal go to Applications > Accessories > Terminal

In that terminal type or copy and past the following command:

```
sudo chown -R yourusername:yourusername /media/sda5/songs
```

If your username on the system is suhu that would be:

```
sudo chown -R suhu:suhu /media/sda5/songs
```

The chown part tells Ubuntu to make the following user the owner with read, write and execute permissions

The -R part tells Ubuntu that the following directory (path to the following directory) and all files and folders inside will be yours. -R stands for recursive

The suhu:suhu tells Ubuntu the user:group to chown the directory to.

The path part should be self explanatory now.

Clear as mud yet? ;)

PS. after running the command, you will be asked for the password, just enter your own password and hit enter (return)

---

