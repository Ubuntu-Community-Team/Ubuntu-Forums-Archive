---
title: "Windows has synctoy for free automated folder sync backup, what is there for linux?"
date: 2007-10-31
forum: General Help
---

### Post by boast on 2007-10-31
The title says it all. In windows, I had automated folder syncs with synctoy from microsoft. I need to do the same for linux.

I don't want any fancy partition compressing encrypting stuff, just a simple folder backup solution GUI with the ability to schedule it to run daily.

thanks.

---

### Post by sloggerkhan on 2007-10-31
Try the simple backup package in synaptic (sbackup or simple backup or something). Or script a cp or dd operation. Or try compiling Conduit and use that (of course it's not a finished system.)  It does depend a bit on what the intent of the system is. If you want to keep copies of a single file as a version changes, I'd say it's a bit different than wanting backup copies of /home, for example.

---

### Post by por100pre1 on 2007-10-31
Try Grsync:

```
sudo apt-get install grsync
```

read the manual on to automate the backups:

```
man grsync
```

press q when finished reading.

---

### Post by boast on 2007-10-31
phew, sbackup seems to be what I wanted.

thanks.

---

### Post by sloggerkhan on 2007-10-31
I'd make sure it works with the setup you want. I know there are some things, such as network drives, that it doesn't like much. So I'd make a backup and check that it worked ok, and maybe look at the documentation before depending on it.

---

### Post by boast on 2007-10-31
ok, sbackup won't work. It creates a .tgz No way im going to be opening up a tgz and extracting a file everytime i want to see it.

I guess grsync will be it.

---

### Post by sloggerkhan on 2007-11-01
See, when I use it I like that feature, but I'm mostly interested in backing up my documents in case of disaster recovery, so I don't really need consistant access. And I don't want backups taking more space than I need. There are a lot of options. Hopefully one works for you.

---

### Post by boast on 2007-11-01
anybody know how to schedule grsync?

Is putting this in crontab the correct way? (daily runs @ 9pm) [color=red]0 21 * * * grsync -e default
[/color] ?

thanks

---

### Post by Spare Tire on 2007-11-01
Hey boast, tell me how it goes with any synching program you try, i need the feedback from somebody who's used to SyncToy.
I need to keep files between my laptop and my desktop up to date. It's not backing up, it's a two way thing, depending from where i work. And it's over a network. And possibly, from windows to linux, or vice versa, or linux to linux, as i multi-boot and my data partition separate from my system partition. Synching between windows and linux is like the final frontier till i put start using linux for real. I need to work on these machines and i don't want to be messing around with stuff i don't know "just for fun" and risking to lose my work.

---

### Post by por100pre1 on 2007-11-01
> **boast said:**
> anybody know how to schedule grsync?

Is putting this in crontab the correct way? (daily runs @ 9pm) [color=red]0 21 * * * grsync -e default
[/color] ?

thanks

Please read [this thread]("http://ubuntuforums.org/showthread.php?t=591875").

---

### Post by boast on 2007-11-01
> **por100pre1 said:**
> Please read [this thread]("http://ubuntuforums.org/showthread.php?t=591875").

yeah thats where I found the "grsync -e default" but since I don't have kcron I do not know if that edits crontab, or makes a cron.daily (or w/e folder) file, or something.

---

### Post by boast on 2007-11-07
well, I did it with gcron. Still can't get it to work

---

### Post by mike555 on 2007-11-07
I don't know if it's what your looking for but you might want to try "Flyback"      ....      [http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)       ... I haven't tried it .

---

### Post by volksman on 2007-11-07
^^^^ looks pretty sweet....but sbackup has a gui for interacting with the tarball.  In fact it's pretty damn slick cause it provides a nice interface for accessing backups AND if you change your mind and decide to go with another solution you don't have to re-pack all your data...just unpack the tarball when you need it....To each their own I guess but I liked it.  

Flyback does look pretty damn cool though...was going to install it today but didn't have time... :)

---

### Post by boast on 2007-11-11
> **boast said:**
> well, I did it with gcron. Still can't get it to work

 .

---

### Post by boast on 2007-11-12
edit; well cron doesn't work for grsync. So I'll just use grsync to create the rsync commands.

we,, if anyone has issues, check my thread: [http://opbyte.freeforums.org/viewtopic.php?p=292](http://opbyte.freeforums.org/viewtopic.php?p=292)

---

### Post by Fevrin on 2008-06-02
One of the features of SyncToy is that it is able to rename files at the destination, which means that instead of deleting the file with the old name and then sending over the same file with the new name, the file would simply be renamed to the new name.   Is there a program out there that can do this?  I've already read through rsync's man page, and there doesn't seem to be an explicit way to do this--perhaps a combination of commands could do it?

Also, SyncToy enables the user to select or deselect individual files/folders to perform operations on (create, overwrite, delete, rename, etc.) before executing the actions.  Does anyone know of a similar feature in a Linux-compatible backup program?

Unfortunately, I haven't been able to get SyncToy 1.4 or 2.0b to run under WINE, as they're both .msi files.  Even after extracting the files within the .msi's, though, WINE won't run them.

---

