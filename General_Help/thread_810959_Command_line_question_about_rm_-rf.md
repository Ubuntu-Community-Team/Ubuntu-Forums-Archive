---
title: "Command line question about rm -rf"
date: 2008-05-28
forum: General Help
---

### Post by dwhs on 2008-05-28
I'm trying to remove a bunch of .core files in several directories.  For now I going to the directory and doin rm -rf core.*  but I would like to be able to run this command for several directories so I was thinking:

rm -rf /home/username/ core.*

But I'm thinking it might just delete everything and not the core.* files

---

### Post by werries on 2008-05-28
i'm afraid of that idea too.
also, you shouldn't need the -rf options. r is for directories, f is for forcing, and you don't want to force it.

---

### Post by MythosLegend on 2008-05-28
If you use 
rm -rf /home/username/ core.*
you will be erasing files like: core.f, core.etc
you will not be erasing files like a.core or b.core.c

If you are unsure about using a command, you could create test documents and try out the command.

---

### Post by inportb on 2008-05-28
Indeed, exactly what I was about to say.

> **werries said:**
> i'm afraid of that idea too.
also, you shouldn't need the -rf options. r is for directories, f is for forcing, and you don't want to force it.

-f is short for --force, but it's not what everyone might think it is:

> -f, --force: ignore nonexistent files, never prompt

---

### Post by geo909 on 2008-05-28
So I guess if he removes the 'f' options he will be asked if he want to remove each file, right?

---

### Post by dwhs on 2008-05-28
> **geo909 said:**
> So I guess if he removes the 'f' options he will be asked if he want to remove each file, right?

I thought of this for testing. But there is thousands of these core files so for the run I would need force. So this might actually work: rm -rf /home/username/ core.*

I will test it. awesome

---

### Post by drs305 on 2008-05-28
> **geo909 said:**
> So I guess if he removes the 'f' options he will be asked if he want to remove each file, right?


No, the -i switch does that: **rm -i** ... :)

---

### Post by dwhs on 2008-05-28
I created a folder called  test55   then added a file in it called core.55  I then went one directory up and ran this: rm -rf test55 core.*

But it removed the test55 folder as well

Maybe there needs to be a absolute path?

So I added the folder test55 in the /directory of the server and ran this: rm -rf /test55/ core.*  but it still removed the folder

---

### Post by dwhs on 2008-05-28
What about this command?  find / -name core.* -exec rm {} \;


Yes this works better for it, thanks

---

