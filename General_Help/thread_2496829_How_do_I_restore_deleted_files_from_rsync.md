---
title: "How do I restore deleted files from rsync?"
date: 2024-04-14
forum: General Help
---

### Post by MariosFFX on 2024-04-14
I used the following command


    > rsync -avh --progress --remove-source-files --delete /mnt/disk-1/* /mnt/disk-2


I thought that `**delete**` would overwrite files in my destination directory. But instead, it deleted the files in the destination directory if they didn't exist in the source directory.


I tried restoring files with `**ext4magic**`, `**extundelete**`, `**testdisk**` and had no luck.


`**ext4magic**`, tries to restore the files but I get `**segmentation fault**` and stops...


Both filesystems are `ext4`


Any programs I could try?

---

### Post by yancek on 2024-04-14
> it deleted the files in the destination directory if they didn't exist. 

I believe a better explanation of what you intended and what happened is required.  Read that statement and think about the logic.  It is not possible to delete files that do not exist!

---

### Post by MariosFFX on 2024-04-14
> **yancek said:**
> I believe a better explanation of what you intended and what happened is required.  Read that statement and think about the logic.  It is not possible to delete files that do not exist!

Corrected. It somehow tried to sync the files. If the file wasn't on the source directory then it would delete it in the destination directory, for example

Source:
source/dir-1/

Destination
destination/dir-1/a.md
destination/dir-1/b.md
destination/dir-1/c.md

The files in the destination didn't exist, so rsync deleted them.


What I tried to do was to merge the contents of directories, I wanted for example:

Source 1:
source-1/dir-1/a.md
source-1/dir-1/b.md
source-2/dir-1/c.md

Source 2:
source-2/dir-1/c.md
source-2/dir-1/d.md


I wanted the following result
destination/dir-1/a.md
destination/dir-1/b.md
destination/dir-1/c.md
destination/dir-1/d.md

And I ended up with empty directories. The above command deleted the files from the destination as well as from the source.

---

### Post by TheFu on 2024-04-14
> **MariosFFX said:**
>  
And I ended up with empty directories. The above command deleted the files from the destination as well as from the source.

To accomplish that, I would have used **rm** instead. Much clearer.

If you want to restore files, use the backup you made before doing anything risky.

Linux (and rsync) follows the UNIX philosophy, which simply asks, "can I do what was asked?"   The program doesn't know if what is being asked is [COLOR="#00FF00"]brilliant[/COLOR] or [COLOR="#FF0000"]stupid[/COLOR], just whether it can take the inputs, honor the options, and create the outputs from those options and inputs.  Seems to me, it did what you asked.

You do know about the *--dry-run* option for rsync, right?
Some key things in the rsync manpage:```

       --remove-source-files    sender removes synchronized files (non-dir)
       --delete                 delete extraneous files from dest dirs
       --delete-before          receiver deletes before xfer, not during
       --delete-during          receiver deletes during the transfer
       --delete-delay           find deletions during, delete after
       --delete-after           receiver deletes after transfer, not during
       --delete-excluded        also delete excluded files from dest dirs
       --dry-run, -n            perform a trial run with no changes made

```
So it appears that then each option is checked matters.  

Also, when doing destructive things, it is important to read all the caveats in the manpage to ensure there aren't any unintended consequences.

If you just want to move files, across file systems, I'd use the '**mv**' command, not **rsync**.  There are a number of ways to locally mount remote storage, if it isn't on the same computer.  **sshfs** would be the worst case, though I wouldn't expect symbolic links to be correct after the move.

---

### Post by hyperlinxe on 2024-04-14
You have two file systems essentially without being aware of the fact, like most people. There is the file system that you are aware of, then there is the file system that you are not aware of, that your storage device uses to arrange data. When you deleted files, in the context of the file system you are aware of, you deleted files, in the context of the file system you are aware of. 

The question you're asking is the big money question, that does not have great answers actually.

---

### Post by dragonfly41 on 2024-04-14
I suggest you use in future grsync (the rsync GUI) and enable "dry run".
And fall back on backups .. in case of disaster.

Why do some discussions remind me of Danny Kaye in the Court Jester?

> 

[LIST]
[*]**[Griselda ]("https://www.imdb.com/name/nm0622450/?ref_=tt_ch"): **Listen. I have put a pellet of poison in one of the vessels.
**[Hawkins ]("https://www.imdb.com/name/nm0001414/?ref_=tt_ch"): **Which one?
**[Griselda ]("https://www.imdb.com/name/nm0622450/?ref_=tt_ch"): **The one with the figure of a pestle.
**[Hawkins ]("https://www.imdb.com/name/nm0001414/?ref_=tt_ch"): **The vessel with the pestle?
**[Griselda ]("https://www.imdb.com/name/nm0622450/?ref_=tt_ch"): **Yes. But you don't want the vessel with the pestle, you want the chalice from the palace!
**[Hawkins ]("https://www.imdb.com/name/nm0001414/?ref_=tt_ch"): **I don't want the vessel with the pestle, I want the chalice from... the what?
**[Jean ]("https://www.imdb.com/name/nm0424318/?ref_=tt_ch"): **The chalice from the palace!
**[Hawkins ]("https://www.imdb.com/name/nm0001414/?ref_=tt_ch"): **Hmmm?
**[Griselda ]("https://www.imdb.com/name/nm0622450/?ref_=tt_ch"): **It's a little crystal chalice with a figure of a palace.
**[Hawkins ]("https://www.imdb.com/name/nm0001414/?ref_=tt_ch"): **The chalice from the palace has the pellet with the poison?
**[Griselda ]("https://www.imdb.com/name/nm0622450/?ref_=tt_ch"): **No, the pellet with the poison's in the vessel with the pestle.
**[Hawkins ]("https://www.imdb.com/name/nm0001414/?ref_=tt_ch"): **Oh, oh, the pestle with the vessel.
**[Jean ]("https://www.imdb.com/name/nm0424318/?ref_=tt_ch"): **The vessel with the pestle.
**[Hawkins ]("https://www.imdb.com/name/nm0001414/?ref_=tt_ch"): **What about the palace from the chalice?
**[Griselda ]("https://www.imdb.com/name/nm0622450/?ref_=tt_ch"): **Not the palace from the chalice! The chalice from the palace!
**[Hawkins ]("https://www.imdb.com/name/nm0001414/?ref_=tt_ch"): **Where's the pellet with the poison?
**[Griselda ]("https://www.imdb.com/name/nm0622450/?ref_=tt_ch"): **In the vessel with the pestle.
**[Griselda ]("https://www.imdb.com/name/nm0622450/?ref_=tt_ch"): **The chalice from the palace has the brew that is true.
**[Jean ]("https://www.imdb.com/name/nm0424318/?ref_=tt_ch"): **Don't you see? The pellet with the poison's in the vessel with the pestle.
**[Griselda ]("https://www.imdb.com/name/nm0622450/?ref_=tt_ch"): **The chalice from the palace has the brew that is true!
**[Jean ]("https://www.imdb.com/name/nm0424318/?ref_=tt_ch"): **It's so easy, I can say it.
**[Hawkins ]("https://www.imdb.com/name/nm0001414/?ref_=tt_ch"): **Well then you fight him!
**[Griselda ]("https://www.imdb.com/name/nm0622450/?ref_=tt_ch"): **Listen carefully. The pellet with the poison's in the vessel with the pestle, the chalice from the palace has the brew that is true.
**[Hawkins ]("https://www.imdb.com/name/nm0001414/?ref_=tt_ch"): **The pellet with the poison's in the vessel with the pestle, the chalice from the palace has the brew that is true.
**[Jean ]("https://www.imdb.com/name/nm0424318/?ref_=tt_ch"): **Good man!

[/LIST]


---

