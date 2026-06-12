---
title: "my files are all gone!"
date: 2007-10-16
forum: General Help
---

### Post by leptons on 2007-10-16
today I was reading some debian tutorial, trying to learn various commands.

then was messing around with the mv command

I typed in
mv hello
mv hello *

I didn't even know why I did that... doesn't make any sense...
anyway, it gives me some error and afterwards i realized that all the files in my folders are gone!!!

is there anything I can do to recover them??? and what exactly have happened?

[SOLVED]
all the files ended up in my Video folder... how weird, I never even typed in Video when I was messing with the commands.

---

### Post by leptons on 2007-10-16
I'm desperately in need of help... I have lost all my important files in Documents... somebody please help me!!

---

### Post by ridgeland on 2007-10-16
mv is rename
$ mv hello
gives an error message no target.
$ man mv
will show the manual page but no mention of a target of *
What tells you all your files are gone?
$ ls
nautilus?

---

### Post by kellemes on 2007-10-16
If *hello* was a file you wanted to move/rename, I guess you lost *hello* also?
So first search for it like so: **locate hello**
This *may* give you the location of *hello *and *may* point you to the other files.

---

### Post by leptons on 2007-10-16
Nevermind, Finally I found out that all the files are moved to the Video folder for some reason... who would've konwn???

I searched for Documents and found nothing... and now it is in Video folder.. talking about weirdness.

[edit: hello wasn't a file... there was nothing named hello...I will never use the * symbol from now on... it only gives trouble..]

---

### Post by ridgeland on 2007-10-16
Was the video folder the current working directory when you issued the command?

---

### Post by leptons on 2007-10-16
no, I was in my home folder at all times... I had nothing in Videos folder so there is really no reason for me to go in there.... This is just really strange...

anyway, thank you for all you guys' help, I'm very surprised on how quickly someone replies my urgent and desperate call for help... thank you.

---

### Post by ridgeland on 2007-10-16
Looks like you issued the move command to a file that didn't exist to a wildcard location.
Better to focus now on how to do backups.
See any need to do backups?

---

