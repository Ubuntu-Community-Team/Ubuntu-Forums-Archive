---
title: "&quot;[init] database is locked&quot; when starting app"
date: 2013-04-08
forum: General Help
---

### Post by kurja on 2013-04-08
I had a gpu-related crash while running [darktable]("http://www.darktable.org/"), and since I have not been able to run the program - trying to start form console, all I get is ```
[init] database is locked, probably another process is already using it

```

I used synaptic to remove darktable and reinstall (to a newer version, actually), but I'm still getting this error message. Any ideas?

---

### Post by kurja on 2013-04-09
any ideas on how to remedy this issue?

---

### Post by Bashing-om on 2013-04-09
kurja; Hi !

What pops to mind is that you have an instance of the package manager open and trying to start another package manager process.
Like, that while synaptic is open, you are running apt-get or dpkg from the command line ?

If you close everything out and reboot, what results from terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
```[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by kurja on 2013-04-09
Hi, thanks for the reply.

Perhaps I should have clarified that I'm getting the error when trying to start Darktable, not when trying to run update, if there was any confusion about that? Synaptic removed and installed the application without any visible hiccups.

I see nothing unusual when running apt-get update and upgrade.

---

### Post by Bashing-om on 2013-04-09
kurja;
Sorry, I too may have jumped to a conclusion,
darktable; Well, Is there an instance of the application autostarting upon booting the system ?
All I can think of presently, As you reinstalled darktable I would think the new install would have overwritten any residual config files from the older version .
I am not at all familiar with darktable, but is there anything in a config file that would start the application ?
maybe look at something like :
```
ps au | grep darktable
``` see if it is running on the system.[INDENT=2]
not much, but a thought

[/INDENT]

---

### Post by kurja on 2013-04-10
> **Bashing-om said:**
> kurja;
Sorry, I too may have jumped to a conclusion,
darktable; Well, Is there an instance of the application autostarting upon booting the system ?
All I can think of presently, As you reinstalled darktable I would think the new install would have overwritten any residual config files from the older version .
I am not at all familiar with darktable, but is there anything in a config file that would start the application ?
maybe look at something like :
```
ps au | grep darktable
``` see if it is running on the system.[INDENT=2]
not much, but a thought

[/INDENT]

that gives me ```
3232  0.0  0.0   5612   832 pts/0    S+   21:18   0:00 grep --color=auto darktable
```
I've no idea what that might mean though :^/

---

### Post by Bashing-om on 2013-04-10
kurja;

The output only shows the invocation of looking for an instance of darktable running. No indication that the application it's self is running.

I am at a loss now as to how to see what all starts when darktable is started. I do not have it installed on my system so not able to look at the config files. As an alternative try this:
Start darktable and then run the "ps" command again, see if there is more than the two expected returns (??}
```
ps au | grep darktable
```
Begs the question "what is locking up what database" ??[INDENT=3]
questions generate answers 
[/INDENT]

---

### Post by kurja on 2013-04-10
[SIZE=2][FONT=arial]Ok, trying to start darktable I get the same "[/FONT][/SIZE][FONT=Ubuntu Mono][COLOR=#000000][SIZE=2][SIZE=2][FONT=arial]database is locked", running ps au etc generates the same response as it did before.

I did post about this at darktable.org/redmine hoping to get advice on what might be afoot, but no responses there so far.

This is bad because I need a processor for my images and certainly am not looking forward to reinstalling everything from scratch [/FONT][/SIZE]:([/SIZE][/COLOR][/FONT]

---

### Post by Bashing-om on 2013-04-10
kurja;
I am reaching here, but let's see if any indications are in /tmp or /var:
Terminal code:
     ```


     
find /tmp -type f -iname darktable -print
``` 
And assuming the ap is starting up in the name as "darktable".
If no return from the "/tmp" directory, try substituting "/var" for "/tmp".

Not starting at all is at least more info than we had.

still think'n

---

### Post by Bashing-om on 2013-04-10
kurja;

Another thought, is this on a NFS-mount ... or directly from the local machine ?

---

### Post by kurja on 2013-04-10
that returns a bunch of of permission denied notifications, running with sudo returns absolutely nothing for both /tmp and /var

---

### Post by kurja on 2013-04-10
> **Bashing-om said:**
> kurja;

Another thought, is this on a NFS-mount ... or directly from the local machine ?

local.

---

### Post by rnerwein on 2013-04-10
hi
ok let's try "strace".
open a terminal and run: strace -f -o bla.txt -e trace=open,fcntl,stat name_how_you_start_your_database
post the output of bla or have a look by yourself at the file. it is plain ascii. you have to look for the fcntl systemcall - looks like
fcntl([COLOR=#ff0000]3[/COLOR], F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=0, len=0}) = 0
go back in the trace until you find the open-call with the file-descriptor (here [COLOR=#ff0000]3[/COLOR])
the open-call looks like: open("blu", O_RDWR)                     = [COLOR=#ff0000]3[/COLOR]
and you can see that the process want to lock "blu". this should be the lockfile.
move this file "blu" to _blu and try to start your database again.
good luck
ciao

---

### Post by stinkeye on 2013-04-10
Could try looking  at your hidden config files in your home directory.
Possibly a .lock file that wasn't released due to the crash.
Maybe delete **~/.config/darktable** if it exists.

---

### Post by kurja on 2013-04-11
> **rnerwein said:**
> hi
ok let's try "strace".
open a terminal and run: strace -f -o bla.txt -e trace=open,fcntl,stat name_how_you_start_your_database
post the output of bla or have a look by yourself at the file. it is plain ascii. you have to look for the fcntl systemcall - looks like
fcntl([COLOR=#ff0000]3[/COLOR], F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=0, len=0}) = 0
go back in the trace until you find the open-call with the file-descriptor (here [COLOR=#ff0000]3[/COLOR])
the open-call looks like: open("blu", O_RDWR)                     = [COLOR=#ff0000]3[/COLOR]
and you can see that the process want to lock "blu". this should be the lockfile.
move this file "blu" to _blu and try to start your database again.
good luck
ciao

output of that strace command is the very same database locked- message

in bla.txt, I found ".config/darktable/library.db", O_RDWR|O_CREAT|O_LARGEFILE, 0644) = 4"

I renamed the file, and now darktable starts!! :o Apparently the database contained just thumbnail images.

[SIZE=3]**Thank you**[/SIZE] all!

---

### Post by Bashing-om on 2013-04-11
kurja;
That is great news, pleased it is resolved. -> strace to the rescue again !
Please mark this thread as "solved" it aids all, those seeking solutions and the helpers time, and keeps the forum tidier.
interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.[INDENT=2]
best regards

[/INDENT]

---

### Post by kurja on 2013-04-11
thanks again - you know, I was just going to post again asking how on earth am I supposed to mark the issue as solved :D I could swear it was under thread tools not a long time ago....

---

### Post by Bashing-om on 2013-04-11
kurja;
solved: Our mods are working on it to make it so once again. [INDENT=2]
Take care and my regards

[/INDENT]

---

