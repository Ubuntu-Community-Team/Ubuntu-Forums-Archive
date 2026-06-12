---
title: "Deleting a corrupted folder"
date: 2007-04-11
forum: General Help
---

### Post by daicoden on 2007-04-11
Hi, recently I had a minor hard drive crash.  The /tmp file pointer was corrupted along with several others which I managed to fix.  The /tmp file still alludes me.  It still displays /tmp when you ask for the directory list in the / directory.  However upon trying to remove it, the system throws a Input/output error.  Is there another way to remove this folder or rename it?  Even if it involves going through bytes i just need to change one character so I can make another one.

Thanks

Matt

---

### Post by Stephen Howard on 2007-04-11
Is /tmp in its own partition?

What type of filesystem is /tmp on?

---

### Post by Stephen Howard on 2007-04-11
oh, and what does the following report:
```

sudo fsck -N /tmp
```

---

### Post by daicoden on 2007-04-11
You'll have to excuse my lack of knowledge for the terminology.

/tmp is on the main partition and only one and is part of the main filesystem along with the /root /home /etc, which is the default one.  I'm not sure how to check.


fsck 1.38 (30-Jun-2005)
[/sbin/fsck.ext2 (1) -- /tmp] fsck.ext2 /tmp

I didn't create /tmp and it seems like all of my server programs try to create files here at some point, for instance I can't access anything in mysql because it fails with an error complaining about a write fail to /tmp

Thank you!

---

### Post by Stephen Howard on 2007-04-12
I may be misunderstanding you - do you actually want to delete /tmp?

Without /tmp your system won't even boot to a graphical user interface (ie gnome, kde etc).  It is critical.

What is the actually problem you are trying to solve?

---

### Post by Stephen Howard on 2007-04-12
Aside from mysql, is any other program complaining?  If so, have a look at the error logs in /var/log/messages and see if there are any clues or further details about instances of i/o failure.  

Perhaps there's a permissions problem stopping /tmp access to some programs.  You can show the permissions by typing:

> ls -al /tmp

(ie both of the 'l' in the above command are lower-case 'L')

---

### Post by daicoden on 2007-04-12
> **Stephen Howard said:**
> I may be misunderstanding you - do you actually want to delete /tmp?

Without /tmp your system won't even boot to a graphical user interface (ie gnome, kde etc).  It is critical.

What is the actually problem you are trying to solve?

Actually, yes I want to delete /tmp and then restore it.  I actually would be happy renaming it to something and making a new one.  I have all of those symptoms.  My graphical user interface won't start I can't update any packages I can't do anything involving /tmp because the pointer to that location is gone.  I had a minor system crash and while fixing it I disconnected that folder from the file system accidentally (I think is what happened)

Problem is I can't run any commands on it as it is not actually there.

Running ls on the folder produces an Input/Output error.

Thanks so much!

---

### Post by Stephen Howard on 2007-04-13
so it doesn't show up if you do a directory listing or is it that you just can't write to it/change it?  If the io issue only comes up when you try to write to /tmp, then it most likely is a permissions problem:  What happens if you type:

> sudo chmod 01777 /tmp


That should make /tmp writeable by every user on the system (which is pretty much what you want) and therefore allow all your programs to create files in /tmp.

If the above doesn't do anything (ie you still get an io error), then you should probably burn a [gparted cd]("http://gparted.sourceforge.net/livecd.php").  Then boot with the cd and that will give you some gui-based software to run error checks / fixes on your hard drive.

---

### Post by daicoden on 2007-04-13
It does show up when i do a directory listing, but no commands will run on it.  Which leads me to believe the name is still in the directory list of the / folder but the pointer of the tmp folder is either bad or null.  I just don't know where all that information is stored or if it accessible.

Running chmod on /tmp causes an Input Output error.  I did have a minor hard drive crash.  I am trying to pull everything off the drive onto a new one.  Unfortunately mysql (which I am trying to pull data off of) seems to require the tmp folder to do the slightest operation.  I believe I accidentally changed the pointer node to the location of the /tmp folder as ubuntu had trouble reading the disk it went through and disconnected all unaccessible child nodes (at least that's what I gathered from the messages).  

I'm really looking for the location of the table that links the directory name to the hard drive memory block.  And then I want to change that to maybe tmz or some character and then make a new /tmp folder so I can get onto my system with Ubuntu's gui and grab everything off.

just a temporary fix if you pardon the pun!

Thanks!

---

### Post by steve196 on 2007-04-13
Did you do all your attempts from the installed system or did you run a live cd, when you tried to delete the folder?
For a live cd the /tmp on the harddisk is not a system folder.

---

### Post by daicoden on 2007-04-13
I will try that, but again the file is corrupted.  I can not get any information about the file it is as if it does not exist.  So I am not sure how trying to run commands will have from a live cd will be of much help as currently simple commands like ls do not work and produce read errors.

but I will give it a shot!  Thanks

---

### Post by Stephen Howard on 2007-04-13
Booting using gparted is entirely in ram, so it does not use the hd at all.  Then you can run 
> fsck /dev/hdXX         (where XX is your hard drive)     The fsck program should be able to fix dangling directories automatically.  

Another option which I guess you've probably already investigated is to us the various ext2 [debug utilities]("http://tldp.org/HOWTO/Filesystems-HOWTO.html#toc6.17") and the [file system editor]("http://tldp.org/HOWTO/Filesystems-HOWTO.html#toc6.19").

Alternatively, it might be best to backup whatever is in your /home directory and then simply do a fresh install of Feisty (which should be released mid next week).

---

### Post by daicoden on 2007-04-13
Alright, thanks so much!  I will do that then!

---

### Post by az on 2007-04-13
You can't just rename it?

---

### Post by daicoden on 2007-04-14
Alas no, I would like to rename it but any system commands that involve getting properties such as permissions of the folder result in an input output error.

so mv /tmp /tmp2 fails

---

### Post by Stephen Howard on 2007-04-14
Another solution might be to leave the dodgy /tmp alone, and instead create an alternate in a subdirectory - maybe /hack/newtmp.  Then you could edit fstab and change/add a /tmp entry that will point to /hack/newtmp

Just remember to give the new /tmp permissions 01777 so that it is world writable.

---

### Post by daicoden on 2007-04-14
Perfect!  I will give that a shot I was about to say I tried the fsck and to my horror it was the same program that caused this problem in the first place.  When I started up my computer one day it said it couldn't load the operating system and asked me to run a manual fsck (I couldn't remember what it was called).  It asked if it wanted to fix the /tmp folder and i said yes, little did I know that meant break the system.

Thank you I will give hacking it a shot!

Matt

---

