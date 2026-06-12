---
title: "Folder Permission"
date: 2013-02-13
forum: General Help
---

### Post by tmcq on 2013-02-13
I've read tons of posts detailing how to change directory ownership so I can add files and folders - but I can't seem to correctly follow the directions that are always given because I don't understand them.

I want to add a track folder (already downloaded) to SuperTuxKart.  The folder where these are located:  (usr/share/games/supertuxkart/data/tracks) is owned by root.

What is the string that I need to enter in terminal to change ownership to me (tmcq - or tmcq@qdesk)?  Whenever I try the variations of chown I can think of I get a missing operand error, or a no file exists error.

---

### Post by hwttdz on 2013-02-13
In general if you're lost about a command type "man commandname", so I've just taken a look at "man chown" and it gives us a few good bits...

Synopsis:
```
chown [OPTION]... [OWNER][:[GROUP]] FILE...
chown [OPTION]... --reference=RFILE FILE...
```

The square brackets mean this is optional.  So in general it wants something like
```
chown owner:group file
```
or
```
chown --reference=file_with_correct_owner file
```

so we know we want ```
chmod tmcq:yourgroup /usr/share/games/supertuxkart/data/tracks
```

We probably don't want to change the folder ownership itself, but the ownership of the contents as well, so from "man chmod" we see that -R, or --recursive will operate recursively.

so that makes it 
```
chmod --recursive tmcq:yourgroup /usr/share/games/supertuxkart/data/tracks
```

but since I don't know your group I might do...
```
chmod --recursive --reference=~ /usr/share/games/supertuxkart/data/tracks
```

Which will make the ownership of that folder the same as the ownership of your home directory.

---

### Post by Bashing-om on 2013-02-13
tmcq; Hi !

Others may have a differing perspective, but, why would you want to put a directory (folder) with less permissiveness under a directory that is that is owned by root ?
I do not know that it is even possible - security restrictions- and I have not tested to see if it is doable.
What is it that you are trying to accomplish ? A shared folder for music ? Perhaps we can advise a better alternative .

[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by bab1 on 2013-02-13
> **tmcq said:**
> I've read tons of posts detailing how to change directory ownership so I can add files and folders - but I can't seem to correctly follow the directions that are always given because I don't understand them.

I want to add a track folder (already downloaded) to SuperTuxKart.  The folder where these are located:  (usr/share/games/supertuxkart/data/tracks) is owned by root.

What is the string that I need to enter in terminal to change ownership to me (tmcq - or tmcq@qdesk)?  Whenever I try the variations of chown I can think of I get a missing operand error, or a no file exists error.
The "string" could be may things depending on what the parent file structure is.  In essence the when directory executable bit is set for the owner, group or others (the 3 entities) that entity may traverse or descend into the directory.  So first you need to make sure all directories along the path (usr/share/games/supertuxkart/data/tracks) have the executable bit set.  Additionally you would need to make sure that you are either the owner of the directory you wish to copy these files to or a member of the group that is the group-owner...or if you don't care make the destination directory read/write for the all (others).

I have plenty of directories under a root ownership that has the group set to the group ***users***.  If you wish to do it this way you will need to chown (or chgrp) and then chmod the directories in the path.

The permissions should be 775 for directories and 664 for files.  BTW - umask does this already.  The default umask is 0002 which results in the above settings.  The user/group/other is more important (chown or chgrp).

IMO I think you should think about relocating the directories */games/supertuxkart/data/tracks  * to a more logical place.  The /usr directory is for Unix System Resources (it doesn't mean user resources),

As you can see there is no simple incantation that you can apply to any and all situations. 

How do you wish to proceed?

---

### Post by 3rdalbum on 2013-02-13
Don't change the ownership of the folder. Simply make yourself root temporarily.

gksudo nautilus

to open a file browser as root.

When the file browser window opens, navigate to the directory you want to put the files into, and then drag them in.

Close the window.

Done.

---

### Post by bab1 on 2013-02-13
> **hwttdz said:**
> In general if you're lost about a command type "man commandname", so I've just taken a look at "man chown" and it gives us a few good bits...

Synopsis:
```
chown [OPTION]... [OWNER][:[GROUP]] FILE...
chown [OPTION]... --reference=RFILE FILE...
```

The square brackets mean this is optional.  So in general it wants something like
```
chown owner:group file
```
or
```
chown --reference=file_with_correct_owner file
```

so we know we want ```
chmod tmcq:yourgroup /usr/share/games/supertuxkart/data/tracks
```

We probably don't want to change the folder ownership itself, but the ownership of the contents as well, so from "man chmod" we see that -R, or --recursive will operate recursively.

so that makes it 
```
chmod --recursive tmcq:yourgroup /usr/share/games/supertuxkart/data/tracks
```

but since I don't know your group I might do...
```
chmod --recursive --reference=~ /usr/share/games/supertuxkart/data/tracks
```

Which will make the ownership of that folder the same as the ownership of your home directory.
You can't do this```
**[COLOR="Red"]chmod[/COLOR]** --recursive tmcq:yourgroup /usr/share/games/supertuxkart/data/tracks
```...did you mean this```
**[COLOR="Blue"]chown[/COLOR]** --recursive tmcq:yourgroup /usr/share/games/supertuxkart/data/tracks
```

Chmod changes the permissions (mode). Chown changes the ownership.  To set up the file structure you need to use both.  If you are going to use group inheritance you also need to use the SGID bit (i.e. 2775 for directories).

---

### Post by tmcq on 2013-02-13
> **3rdalbum said:**
> Don't change the ownership of the folder. Simply make yourself root temporarily.

gksudo nautilus

to open a file browser as root.

When the file browser window opens, navigate to the directory you want to put the files into, and then drag them in.

Close the window.

Done.

This was the solution I was looking for. Worked perfectly - thanks!

---

### Post by 3rdalbum on 2013-02-14
> **tmcq said:**
> This was the solution I was looking for. Worked perfectly - thanks!

You're welcome.

---

