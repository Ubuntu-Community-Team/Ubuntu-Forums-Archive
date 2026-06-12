---
title: "USB jump drive has become read-only?"
date: 2007-03-06
forum: General Help
---

### Post by bg1256 on 2007-03-06
In Ubuntu Edgy, I was transferring a few documents from one computer to another using my USB jump drive.

However, I can't delete any of the information on it from the trash because it tells me it's read only.  When I right click on it, go to properties, and attempt to change the permissions, it does not allow me to do so.

Ideas?

---

### Post by tribble222 on 2007-03-06
Sounds like the permissions got messed up.  To fix the permissions you need to run a few commands from the terminal.

The following commands assume the location of your mounted USB drive is /media/USB (it's probably in the media folder but called something else) and that your username is bg1256.

To give read/write permissions to the owner of a certain file or folder on the USB drive enter:

```
$ sudo chmod 755 /media/USB/myfile.xxx
```

To change the permissions of everything on the USB drive run:

```
$ sudo chmod -R 755 /media/USB/
```

To make sure you own the file, the above commands work, except replace "chmod" with "chown" and "755" with "bg1256" if that's your username.

Check out the chmod and chown man pages if you want more info!

---

### Post by bg1256 on 2007-03-07
Yes, the permissions are definitely the problem.

However, how do I determine what the proper name for the USB drive is?  It's listed in /media, but it's listed as a custom name, not as sda1, for example.  Am I looking for the mount point, and if so, how do I find it?

---

### Post by tribble222 on 2007-03-07
Yep you're looking at the right folder.  You don't need to worry about any /dev stuff.  Just use the name it has in /media

---

### Post by bg1256 on 2007-03-07
> **tribble222 said:**
> Yep you're looking at the right folder.  You don't need to worry about any /dev stuff.  Just use the name it has in /media

The name it has in media does not work... when I fist got this jumpdrive, I used it on a Mac, and it allowed me to give it a custom name, and I named it my first and last name.  So, it looks like this: JOHN SMITH (name's not John, but you get the idea).

When I enter my name after /media/ in the command, it does not recognize the command.

---

### Post by bg1256 on 2007-03-07
a little bump before I leave for vacation...

---

### Post by tribble222 on 2007-03-07
When using spaces in the command line you need to escape them with a backslash or else it gets confused.

For example, if your name is First Last, you'd enter 

$ sudo chmod 755 /media/USB/First\ Last/

---

### Post by bg1256 on 2007-03-07
Thanks for the tip with the backslash. That allows me to run the commands in the correct place, at least. However, both chown and chmod both get hung up at the same place each time I run them...

---

### Post by tribble222 on 2007-03-08
What do you mean they get hung up?  You can add a -v option for verbose output to help you identify any problems they are having.

---

### Post by jms1989 on 2007-03-08
> **bg1256 said:**
> In Ubuntu Edgy, I was transferring a few documents from one computer to another using my USB jump drive.

However, I can't delete any of the information on it from the trash because it tells me it's read only.  When I right click on it, go to properties, and attempt to change the permissions, it does not allow me to do so.

Ideas?

My /media/ folder is chmoded to 777 and it's sub-directories are also chmoded 777. The purpose is to allow the normal user to plug in or insert a CD/DVD and it should mount once the drive is accessed by the user. 

Also, don't include your CD/DVD drives and USB drives in the /etc/fstab file. Doing so will pervent you from mounting the disk under YOUR username, NOT root. Even if the folder is chmoded to 777.

Hope this helps,
jms1989

---

### Post by bg1256 on 2007-03-20
> **tribble222 said:**
> What do you mean they get hung up?  You can add a -v option for verbose output to help you identify any problems they are having.

I simply mean that it freezes.  I left it going for nearly an hour, and the progress simply stopped working.

---

### Post by bg1256 on 2007-03-20
I think I should be more clear.

When I run:

sudo chmod -R 755 /media/JOHN\ SMITH/

It freezes at the same folder everytime, and my processor spikes to 80%.  Yet, nothing happens, and I've left it this way for nearly an hour.

---

### Post by jms1989 on 2007-03-20
> **bg1256 said:**
> I think I should be more clear.

When I run:

sudo chmod -R 755 /media/JOHN\ SMITH/

It freezes at the same folder everytime, and my processor spikes to 80%.  Yet, nothing happens, and I've left it this way for nearly an hour.

Take out the -R

sudo chmod 755 /media/JOHN\ SMITH/

---

