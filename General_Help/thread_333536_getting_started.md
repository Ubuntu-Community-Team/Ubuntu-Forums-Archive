---
title: "getting started"
date: 2007-01-07
forum: General Help
---

### Post by aisle_s on 2007-01-07
I installed Ubuntu (Edgy Eft) yesterday as a fresh installation. This is the first experience I've had with any *nix OS.

I am not a computer buff by any stretch, but I know my way very well around Windows, and relatively well around computers in general, but that's not so for the rest of my family. So, I'd like to configure a few things just to make the computer safe yet still useable.

Anyways, my problems. I have a second drive mounted to /media/drive-two, and I would like this to be the main storage drive for my family. 

I would like to keep the permissions on my Filesystem high, so only root can access, which pretty much means I would be the only one screwing around in there. Anyways, basically what I want to know is if I can make a link from "Places > Computer" to /media/drive-two so that the rest of my family knows where their storage is without navigating through the Filesystem (they're all used to the Windows layout of drive C:, D:, etc.)

I've tried alot of things to get this drive to show up in "Places > Computer" like the cdrom and floppy do, but nothing has worked! Please help~

---

### Post by meng on 2007-01-07
I'm not sure what "lot of things" you've tried, but it should work if you just navigate to /media/drive-two and then Bookmarks > Add Bookmark (ctrl-D)

---

### Post by aisle_s on 2007-01-07
The bookmark worked, but I was hoping that I could put it in the main window of Computer instead of at the sidebar. Oh well, maybe I'm just being picky ;p

Also: Does anyone know why I am unable to write/read from this second drive? The permissions are set to:

owner: root -> create and delete files
group: users -> create and delete files
other: -> access files

I am unable to create or delete files on this account, which is under the main group "aisle" but is also part of the users group, yet I still can't create files in /media/drive-two.

---

### Post by kebes on 2007-01-07
The commandline way of fixing this:
Open a terminal (see [here]("http://psychocats.net/ubuntu/terminal") if you don't know what that means), and type this:
```

more /etc/fstab

```

You should see an output like:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc              /proc                 proc    defaults             0       0
/dev/sda1      /                        ext3    defaults,errors=remount-ro 0       1
/dev/sda2      /media/drive-two ext3    defaults                  0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

In particular if your partition "media/drive-two" is still just "defaults" you want to fix that. You should then open this file in a text editor:
```

sudo nano /etc/fstab

```

I think you need to change the line for your "/media/drive-two" and replace "defaults" with:
auto,users,rw,exec

Then exit out of the nano editor (Ctrl+X and then say yes for saving).



The graphical way:
I'm a KDE not Gnome user so I'm not sure what the menu items are called (can someone else help), but on the menu find something like "System Settings" and then something like "Disk & Partitions" or "Filesystems". Inside that panel, find your "/media/drive-two" and click "modify" (you may need to enter "administrator mode" first).

Then where it has an entry for "options", add what you need... something like "auto,users,rw,exec".

---

