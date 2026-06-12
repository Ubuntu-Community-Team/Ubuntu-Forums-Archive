---
title: "How do i use the terminal"
date: 2007-08-21
forum: General Help
---

### Post by sarahsilverman on 2007-08-21
i still don't know how to use it fully. i don't know how to cd into filesystem. i type cd Filesystem, yet nothing happens. what do i do?

thanks any help is greatly appreciated :popcorn:

---

### Post by sarahsilverman on 2007-08-21
> **sarahsilverman said:**
> i still don't know how to use it fully. i don't know how to cd into filesystem. i type cd Filesystem, yet nothing happens. what do i do?

thanks any help is greatly appreciated :popcorn:

scratch that, something does happen but it doesn't produce what i want. i want to switch into the filesystem because i have a command i want to use.

this is the command;

sudo chmod 0777 /media/samba

---

### Post by russell.h on 2007-08-21
You oughtn't need to switch into the file system. When you open the terminal it will be in /home/<yourname>, but that command specifies an exact path so you shouldn't need to cd anywhere.

Be careful screwing with permissions though, unless you have some idea what you're doing. Since you clearly got that command from somewhere then I have to assume that someone who does know what they're doing instructed you to use it, but don't just go messing with random files. In linux "everything is a file", so not only can you mess up your OS's ability to access certain hardware, you can mess up config files, and all sorts of other stuff. Generally anything in /home/<yourname> is somewhat expendable, because at worst you can delete your user and re-create it without doing permanent damage to your OS, so if you want to play with the command line stay in there for a while.

---

### Post by sarahsilverman on 2007-08-21
> **russell.h said:**
> You oughtn't need to switch into the file system. When you open the terminal it will be in /home/<yourname>, but that command specifies an exact path so you shouldn't need to cd anywhere.

Be careful screwing with permissions though, unless you have some idea what you're doing. Since you clearly got that command from somewhere then I have to assume that someone who does know what they're doing instructed you to use it, but don't just go messing with random files. In linux "everything is a file", so not only can you mess up your OS's ability to access certain hardware, you can mess up config files, and all sorts of other stuff. Generally anything in /home/<yourname> is somewhat expendable, because at worst you can delete your user and re-create it without doing permanent damage to your OS, so if you want to play with the command line stay in there for a while.

okay, i found the problem. the samba folder doesn't exist. it doesn't show in the browser. but when i try to create it, it says i can't create the folder because it exists. its really weird. im gonna make a new thread.

thank you very much for helping, :guitar:

---

### Post by russell.h on 2007-08-21
Ok, I'm not sure exactly what you're trying to do, but I'm going to go out on a limb and guess that you are trying to create a folder that will be shared via samba.

I think your problem might have something to do with the fact that /media is where Ubuntu likes to mount things. Forgive me if I'm wrong, but I'm going to assume for a minute here you are coming from windows:

In windows the file system goes something like this:

My Computer
-C:
--Folders
-D:
--Folders

In linux things are a bit different. You just sort of have one big conglomerated mass of files, all of which exist someplace relative to the "root" (denoted with a front slash: / ) of the file system (not to be confused with the root user, which is sort of the God of all user accounts). Your main hard drive will probably be mounted directly at root, so folders on it (home, usr, var, and so on) will appear directly within root, as /home, /usr and /var. If you have other hard drives you can specify where they should be "mounted" (in a partition editor, and maybe from within the operating system itself), but by default they get mounted into /media.

For example on my dual boot computer my windows drive gets mounted in /media/sda1. So if I want to access Documents and Settings in C Drive I have to go to "/media/sda1/Documents and Settings" (the quotation marks are necessary if you use this in a command because of the spaces in the folder name).

Not knowing anything about what you are trying to do its a bit hard for me to say, but if you are trying to take a hard drive which is being mounted at /media/samba and share it with samba then the first step is to create a mount point with:
```
sudo mkdir /media/samba
```
Next you will need to actually mount the drive there, which is something that I am not confident enough in my memory to try to tell you how to do.

If on the other hand you are trying to create a folder on your main hard drive that is shared via samba then run the above command anyway, then set up Samba (there are various threads on it around here, it involves editing /etc/samba/smb.conf), then right click on the folder you created in the file browser and go to its sharing preferences and select that you want to share it via samba.

Sorry I just presented either an overwhelming amount of data very little of which applies to you, or an unhelpful trip back to the basics if you are actually an accomplished linux user.:lolflag:

---

