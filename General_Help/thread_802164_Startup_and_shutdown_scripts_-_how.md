---
title: "Startup and shutdown scripts - how?"
date: 2008-05-21
forum: General Help
---

### Post by _kresten on 2008-05-21
Hi.
I've written a couple of scripts that create a local backup and uploads the most resent edition of my thesis to a folder on the interwebs. As it is right now I have to execute them myself, though. So what I would like to do is to add them to my startup and shutdown procedures respectively. I've followed [these]("http://ubuntuforums.org/showthread.php?t=792211&highlight=add+startup+script") [two]("http://ubuntuforums.org/showthread.php?t=70262&highlight=add+shutdown+script") treads' advice, but none of them seem to run my scripts...

Are the treads wrong (I'm especially not sure of the second one). Or have I done something wrong?

Oh, and yes my scripts are working ;-)

---

### Post by Gunman1982 on 2008-05-21
Never did something like mentioned in the first thread but the second one is right.
But I can't say if/what you did wrong if you don't say what you did ;) 

It would be of help to see the scripts too, since even if they work when you execute them as normal user it doesn't mean they work on boot time. As a normal user you have a variable set named $PATH (you can see in a terminal with 'echo $PATH') so if you use some commands without absolute paths linux will lokk in the directorys specified by $PATH. The scripts in rc... don't have such a variable set, so you should use absolute filepaths in them.

---

### Post by Gunman1982 on 2008-05-21
> **Gunman1982 said:**
> Never did something like mentioned in the first thread but the second one is right.
But I can't say if/what you did wrong if you don't say what you did ;) 

It would be of help to see the scripts too, since even if they work when you execute them as normal user it doesn't mean they work on boot time. As a normal user you have a variable set named $PATH (you can see in a terminal with 'echo $PATH') so if you use some commands without absolute paths linux will lokk in the directorys specified by $PATH. The scripts in rc... don't have such a variable set, so you should use absolute filepaths in them.

In addition there should be a README in /etc/rcx.d (i.e. /etc/rc5.d/README)

damn wanted to edit, sorry wrong button -.-

---

### Post by mrprefect on 2008-05-21
Depending on what your scripts are doing and how you use your PC. 

If they are something you only want to run from time to time why not just make a shortcut to the script on your desktop? nice simple click to do it. and no need to run things that don't need to be run.

If you simply want to up and down the files when you turn your say laptop on and off then you should be able to add the script to the /etc/rc.local or even creating a script in the /etc/init.d that will ftp/rsync/scp the files to were you want. 

If you have a system running all the time and want to update daily you might try adding the script to the /etc/crontab and setting a time to auto-update

---

### Post by _kresten on 2008-05-21
Gunman1982>> Yeah, I thought about the paths too. But I did use absolute paths (I even tried running the scripts from different locations just to make sure).

But thanks for confirming the [shutdown]("http://ubuntuforums.org/showthread.php?t=70262&highlight=add+shutdown+script") method. And I'll definitely check out the readme.

---

### Post by MikeEvans on 2008-05-21
All you ever wanted to know about startup and shutdown scripts:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html")

---

### Post by _kresten on 2008-05-21
mrprefect>> The scripts (one for backing up locally and getting the files from a server and the other backing up locally and putting the files on the server) are using tar to backup a directory locally (with an appended date to the filename so I have one for each day at the office) and wget and curl respectively to down- and upload. Thats it. Very simple.

I use the computer at my office and turn it off every day, which is why I thought is was smarter adding the scripts to my startup and shutdown sequences.

---

### Post by _kresten on 2008-05-21
MikeEvans>> Thanks. I'll check [it]("http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html") out!

---

