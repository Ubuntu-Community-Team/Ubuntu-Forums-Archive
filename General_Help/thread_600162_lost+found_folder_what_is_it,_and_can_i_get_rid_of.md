---
title: "lost+found folder: what is it, and can i get rid of it"
date: 2007-11-02
forum: General Help
---

### Post by notatoad on 2007-11-02
is it safe to delete a lost+found folder?  i'm just trying to clean up my tv and movie drives, and they have the lost+found folder in them.

---

### Post by mahousaru on 2007-11-02
It is use to store any files that were saved during failures.  Check if the contents are needed and delete what you don't want.  I would leave the directory alone, but i believe it gets recreated.

---

### Post by mdpalow on 2007-11-14
could someone pls verify the above comment in that Linux will create a ' lost+found ' folder if/when it needs it? Therefore, deleting it would not be a problem.

Also, can someone verify the Lost+Found folders are by DEFAULT created and located in:

/lost+found
/home

when you make a clean install....

thanks...

---

### Post by TidusBlade on 2007-11-14
I think it's created when you create the ext3 partition, happened with my External HD and another partition...

---

### Post by mdpalow on 2007-11-14
good. thanks for that. Your post made me check another partition and sure enough it's there as well.

So is it safe to say the lost+found folder will be found in each partition, but we wouldn't find it placed within another folder? Meaning, this lost+found will always be found at / for that partition?

Also, deleting this folder has no impact then, right.... it would just be re-created if needed by the system?

Basically, I want to know 'cause I do not want to back this folder up and when I restore, I don't want to have to re-create this folder if not necessary.....

Thanks....

---

### Post by TidusBlade on 2007-11-14
To my experience, It recreates itself, I dont think you'll find it in other folders, unless if maybe the program saves its failures in another folder or something. the lost+found would always be found at the / of any ext3 partition. 
So im guessing nothing bad will happen if you delete the folder, but to be on the safe side, I would just delete the files contained inside it.

---

### Post by mdpalow on 2007-11-14
thanks TidusBlade...

I'm not actually wanting to delete it, I just want to omit it during a backup and then not re-create the lost+found folder upon a restore. I realize this is probably the same thing as deleting it in that it's not there any more when you recover. Any further thoughts?

Can anyone else weigh in on this as well?

---

### Post by qamelian on 2007-11-14
This folder is a standard part of the Unix/Linux filesystem hierarchy. See [http://www.cs.wayne.edu/labPages/Unix_T/file_organ.html](http://www.cs.wayne.edu/labPages/Unix_T/file_organ.html) for more details. It doesn't clarify whether or not it will be automatically recreated. Personally, I would leave it alone since it is, in fact, a directory that *nix expects to find.

---

### Post by chrisccoulson on 2007-11-14
FWIW, I always include the folder in backups, as it's usually empty anyway.

---

### Post by mdpalow on 2007-11-14
Thanks very much to everyone replying ...

---

### Post by disturbedite on 2007-11-14
yes, for some reason fsck recreates that folder when scanning if it doesn't find it.

---

### Post by Venoseth on 2008-01-25
I'm really new to this, so please forgive my ignorance, but would setting it as hidden do anything to it? Other than not seeing it myself, I don't see how that could possibly be a bad thing...but you never know.

---

### Post by Venoseth on 2008-01-25
Oh, is putting a . in front of the folder the only way to make it hidden? I guess that changing the name would still cause it to be re-created like normal every time, or is ubuntu smart enough to recognize .lost+found as lost+found...?

---

### Post by chrisccoulson on 2008-01-25
> **Venoseth said:**
> Oh, is putting a . in front of the folder the only way to make it hidden? I guess that changing the name would still cause it to be re-created like normal every time, or is ubuntu smart enough to recognize .lost+found as lost+found...?

No, I don't think you can rename it to '.lost+found'. If you want to hide it in Nautilus though, what you can do is create a file called /.hidden. Then add 'lost+found' to the file. This should cause nautilus to hide the folder. You can hide other files / folders doing this. Just add their names to new lines.

---

### Post by Venoseth on 2008-01-28
That worked, making the .hidden file then adding lost+found to it got rid of it. Wahoo, thanks. n_n

---

### Post by articpenguin on 2008-01-28
when jfs and reiserfs are first created there is no lost+found folder. But the filesystems do create them when a file is damaged.

---

