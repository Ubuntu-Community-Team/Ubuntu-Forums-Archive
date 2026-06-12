---
title: "Make Rsync synchronize file just one time"
date: 2013-02-20
forum: General Help
---

### Post by zabimaru27 on 2013-02-20
Hi everybody. 

So here is my issue. 

I have a script to make Rsync synchronise some of my file between two remote servers in a cron job

But when i cut a file from the destination one, rsync will re synchronize it at the next time the script will be launch by cron.
Is there is a way (directly in rsync or in my shell script) to tell it, if you already threat this file, don't synchronize it again, even if it's not on the destination server anymore ?


thx for your future answered

---

### Post by papibe on 2013-02-20
Hi zabimaru27. Welcome to the forums ):P

I'm afraid after reading your post several time, I can't quite understand your concern.

Could you post your script?

Could you explain it with an example?

Regards.

P.S.:
> **zabimaru27 said:**
> 
But when i cut a file from the destination ...
You mean cut as in deleted, or that you edited it and removed part of it?

> **zabimaru27 said:**
> 
... destination one,...
How many destinations do you have?

---

### Post by zabimaru27 on 2013-02-21
Hi, and thx for your answer. 

My script is quite simple

```

if [ -e /volume1/application/automate/rsyncjob.lock ]
then
  exit
fi

touch /volume1/application/automate/rsyncjob.lock

rsync -auv ******@*****.*******.com:/media/sde1/home/blackmessor/priv /volume1/telecharger

#delete lock file at end of your job

rm -f /volume1/application/automate/rsyncjob.lock

```


So , my concern is i have two servers. 
Server SOURCE and server DESTINATION

My script works well, and it synchronises SOURCE to DESTINATION

but when i get my files in my DESTINATION server (which is a local server in my home), i would like to move this files to put them in my own folders to organize them. 

But if i do that, the next time the sript will be launch, rsync will detect the file is not on DESTINATION anymore (as i moved it) and will resynchronize it again. 

I want to avoid that, like if it could remember (I already synchronise this file once, so i don't do it again, even if it disapear from DESTINATION)

I think it's not possible just with rsync, but maybe it is possible to my script to add each file synchronise with rsync in the exclusion file of rsync ???? Just an idee


Thx

---

### Post by sudodus on 2013-02-21
If you want to 'move these files to put them in your own folders to organize them', and those folders are in the same partition, you can use hard links. That means that the files reside on the same (one and only place) in the file system, but two (or more) addresses point at them.

This way you can keep the files where rsync put them, and at the same time organize them in folders as you like, and rsync should see that they are still there.

Try this method, I think it will work :-)

See ```
info ln
``` to learn about hard links (as opposed to symbolic links).

---

### Post by Paddy Landau on 2013-02-21
> **sudodus said:**
> … you can use hard links.
That is a good idea, but only on two conditions.

[LIST=1]
[*]The destination and your home folder are on the same partition. Otherwise, you can use a symbolic link, which would work as well.
[*]You do not change the file once you have copied it to your home folder (on either the source or the destination). Otherwise, [FONT=Lucida Console]rsync[/FONT] will synchronise it again.
[/LIST]
It would be possible to write a script to remember synchronised files, but this is quite a complex solution.

Alternatively, you can use the [FONT=Lucida Console]--exclude[/FONT] option for [FONT=Lucida Console]rsync[/FONT], but you'd have to keep it manually updated. To simplify things, you can use [FONT=Lucida Console]--exclude--from[/FONT] instead of [FONT=Lucida Console]--exclude[/FONT].

---

### Post by zabimaru27 on 2013-02-21
thx for your answers

> Alternatively, you can use the --exclude option for rsync, but you'd have to keep it manually updated. To simplify things, you can use --exclude--from instead of --exclude.

This is the solution i thought, but i don't know how to get the output of the file name when rsync synchronise it.

---

### Post by sudodus on 2013-02-21
***Edit***: You can perform a 'dry verbose run' with ```
rsync -avn
``` right after you have moved your files. That will show which files it 'would like to sync', and you can add them to your exclude list.

But I still think it is a better idea to link your files instead of moving them

---

### Post by Paddy Landau on 2013-02-21
> **zabimaru27 said:**
> … but i don't know how to get the output of the file name when rsync synchronise it.
I thought you wanted to exclude a file only after you have moved it away from the destination? If that is the case, you'll know the file name, because you moved it. Manually add it to the file that you are using with [FONT=Lucida Console]--exclude-from[/FONT]. Remember to use the full path, otherwise you may accidentally exclude like-named files from other paths.

---

### Post by markbl on 2013-02-21
OP, regarding your script, I would put that lock file in /tmp so that it is ensured it is deleted after a system boot. Also look at the bash builtin "trap" command to ensure the lock file gets deleted for all script exit conditions. And add --delete to your rsync command if you really want to synchronise the source to destination.

---

### Post by Paddy Landau on 2013-02-22
> **markbl said:**
> OP, regarding your script, I would put that lock file in /tmp so that it is ensured it is deleted after a system boot. Also look at the bash builtin "trap" command to ensure the lock file gets deleted for all script exit conditions. And add --delete to your rsync command if you really want to synchronise the source to destination.
All excellent suggestions, especially the [FONT=Lucida Console]trap[/FONT] command.

I would add that to reduce the time to create the temporary file (and reduce the chance of a race condition failing), place it in RAM instead of [FONT=Lucida Console]/tmp[/FONT]. The RAM folder [FONT=Lucida Console]/run/shm[/FONT] already exists and is available for use.

An even better option for locking: use [FONT=Lucida Console]flock[/FONT], which is designed explicitly for this purpose.

---

