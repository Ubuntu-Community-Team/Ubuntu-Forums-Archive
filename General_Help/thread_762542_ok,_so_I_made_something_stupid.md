---
title: "ok, so I made something stupid"
date: 2008-04-22
forum: General Help
---

### Post by lorinbogdan on 2008-04-22
Please help. 

I had the great idea of writing "sudo chmod <<user>>: -R ./* " and providing <<user>>'s password, and now all the files and folders on the harddisk are owned by <<user>>. There are certain things which I can't do, e.g. sudo itself, because /etc/sudoers is now ownwd by UID 100 instead of UID 0.

But there are other things which can be done, e.g. logging in as <<user>> and starting the web browser...

How do I revert to the previous state? And do explain, please. What habve I just done?

Thank you very much,
LorinBogdan

---

### Post by duckville on 2008-04-22
I find it strange that the command you posted actually even executed...
are you sure you didn't type: "chown" rather than "chmod".
what was your pwd when you issued that command...? (was it /)
I don't think there is a way to reverse/undo this.... sorry.

btw:
can you login via "sudo -s"...?
I think what you can do is to use a live CD, mount the partition and then you can revert it that way. The easiest way is a re-install, but it's not the only way.

---

### Post by justleen on 2008-04-22
there is no easy way to reverse this.. you need to set all file permission back to the origial values, which is kinda impossible if you dont have a mirror system or a backup..

---

### Post by hvc123 on 2008-04-22
i dont know if this would work but its worth a go if you are thinking of rebuilding.

boot in single user boot (-s at the end of the kernel line) do not ctrl-d to continue put your root password in. if you have not got root enabled then you will need to boot into live cd and chroot in then change the root password
as root
cd /
chown -R root:root * 
chmod -R 755 *


this will hopefully change everything back to a useable state.
you will have to chown and chmod your users /home areas but it should be pretty much back to normall after that

---

### Post by justleen on 2008-04-22
no, that wont work.. there are more uers and groups then just root.. take haldeamon, that has its own group. changing ownership to root, will make it impossible or haldeamon to read its own files..
you could add all groups to root in /etc/group...

---

### Post by hvc123 on 2008-04-22
yer thats why i said set perms to 755 at least that way other will have execute and read. 

then you might be able to drill down the permissions later.

the other way is obvious if you aint got much on there then rebuild time

---

### Post by justleen on 2008-04-22
> **hvc123 said:**
> yer thats why i said set perms to 755 at least that way other will have execute and read. 

then you might be able to drill down the permissions later.

the other way is obvious if you aint got much on there then rebuild time

yea.. youre  right with that.. chown everything root will give a kinda workable system, more so then what the OP has now any way :)

---

### Post by ibuclaw on 2008-04-22
Only way is to fully re-install your system.

But before we do that:
Boot into your Gutsy/Hardy LiveCD.
Mount your Ubuntu Filesystem.
```
 sudo mount /dev/sda1 /media/ubuntu 
```
If you have a separate home partition, mount it inside the Ubuntu Filesystem.
ie:
```
 sudo mount /dev/sda2 /media/ubuntu/home 
```
Then chroot to your filesystem (This will put you into your Ubuntu Install remotely from the LiveCD):
```
 chroot /media/ubuntu 
```
And save your list of installed packages to your home folder.
```
 dpkg -l | awk '{if ($1=="ii") print $2" "}' | tr -d '\n' > /home/installedpackages
```

And backup your home folder.
```
 cp /home /media/BACKUP/home.bak -R
```
And reinstall your system.

Then once you've re-setup all your user accounts and restored their previous settings, find the "installedpackages" file.
And type in:
```
 sudo apt-get install `cat installedpackages`
```
And your Done!
Everything should be restored back to (almost) normal :)

Regards
Iain

---

### Post by lorinbogdan on 2008-04-22
OK.

1) yes (of course) it was a chown command, and not a chmod one, sorry

2)but thid system works, it boots (what looks like) a normal boot, logs in into the X Window, and so on. The only things which I can't do (up until now) is the sudo command and see/open/modify files that existed previously (which renders the whole thing kinda useless), thank goodness it was a newly installed system

B.

---

### Post by duckville on 2008-04-23
8.04 is out tomorrow,
I'd say you've got a very good reason to use it.

8.04..... here we come...!!!

---

### Post by sdennie on 2008-04-23
> **lorinbogdan said:**
> And do explain, please. What habve I just done?


The above posts are correct.  However, are you sure the command that you ran wasn't: "sudo chown -R user .*"?  If so, what happened is that ".*" matched ".." all the way up to / at which point it recursed over the entire filesystem.  It's a fairly common mistake but, one you are only likely to make once...

---

### Post by lorinbogdan on 2008-04-23
:) OK duckville, thanx... News is I rebuilt my old 7.10, 'cause I had tried some solution advertized here and eventually end up worse.

But now I'm cool, thank you guys!
B.

---

