---
title: "command to move music files out of sub-directories"
date: 2007-10-02
forum: General Help
---

### Post by piusvelte on 2007-10-02
This is a newbie question that has been difficult for me to search on, probably because of how specialized it is. I'm trying to move all of my music files from the album directories, up to the artist directories. Could I run something like this to do that, running from the parent /music directory?

find . -type d -exec cd {} find . -type d -exec cd {} find . -type f -exec mv {} ..  \;

Basically, can you nest "-exec".

Afterwards I'd like to clean up those empty album directories, perhaps with something like this:

find . -type d -exec cd {} find . -type d -exec rmdir  \;

I'm expecting the above to find any artist directories, cd into them, find any album directories, cd into them, mv the files out to the artist directory, and continue to do this for any album and artist.

Overwriting duplicate filenames is OK. Are there any suppress prompt flags that I should use?

I haven't written any shell scripts, but I'm completely open to starting as I've written countless dos batches.

Any help or suggestions would be greatly appreciated!

---

### Post by xplode on 2007-10-02
hello, my first post here. i'd so something like this:

```

> find . -type f -name \*.mp3 | while read f; do d=$(dirname "$f"); d=$(dirname "$d"); m=$(basename "$f"); mv "$f" "$d/$m"; done

```

i.e. pass a list of found files to a subshell. the double dirnames will figure out the parent directory. if you do manage to go the nested-find route (which i don't think will work the way you're written it) you'll have to worry about depth-first searches etc i.e. will you find a file you've just moved, and move it again, or leave it be after the first move.

the subshell here receives one list of files, and works on that.

put an echo before the "mv" to sanity check.

---

### Post by piusvelte on 2007-10-02
Thank you xplode!

I removed the -name as not all of the songs have a .mp3 extension. I just ran a test in a mock directory and it ran perfectly.

Next, I need to script a way to remove the album subdirectories. I'm looking into how to write that now.

---

### Post by piusvelte on 2007-10-02
OK, 2 attempts, one worked, and the other didn't, in testing:

Successful:
```

find . -type d -empty -exec rm -rf {}  \;

```

Unsuccessful, but more fun to write:
```

find . -type d -empty | while read d; do b=$(basename "$d"); rm -rf "$b"; done

```

I'd like to know what I did wrong with the 2nd attempt, but ultimately, I can accomplish my goal.

---

### Post by xplode on 2007-10-02
i think you would have been fine if you didn't do the basename part. find will return the full path (from where you are) to the empty directory (example ./artist/album). the rm will run from the same location as the find, so it needs the full path to the dir to remove, but you're giving it the basename only (album) which doesn't exist in ./ where you're at.

anyway, the first one is cleaner.

---

### Post by piusvelte on 2007-10-02
Perfect. Thanks again xplode!!!

---

