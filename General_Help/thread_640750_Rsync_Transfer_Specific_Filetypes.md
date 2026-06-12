---
title: "Rsync Transfer Specific Filetypes"
date: 2007-12-14
forum: General Help
---

### Post by bsalt on 2007-12-14
Hey, I noticed in rsync's man page that you can specify certain filetypes to be copied, rsync then will not recurse into other directories.

Here's the example - I want to copy my music from my Windows partition into my Ubuntu partition. However, I do not need the Windows system files, like thumbs.db, desktop.ini, and so on. I would only like to copy the music files and directories. Here is the command I tried at first to transfer only .mp3 files (from within my Windows "My Music" folder already):

```
rsync -rP *.mp3 /home/jonathan/Music
```

The "-r" is supposed to trigger rsync to go into every subdirectory, but the *.mp3 causes it to stop only at the root directory (where I have 9 mp3 files). I have 200 sub-folders for each artists, and multiple sub-folders in those sub-folders. Clearly, this would not work out the way I want it to. Is there another command I could give rsync to copy only the folders and filetypes I want copied? Right now, I have it copying everything still, and then I'll just search through and remove the files I didn't want, but I'm sure rsync can do that already, right?

---

### Post by phylae on 2007-12-15
This is from man rsync

> 
a  "*"  matches  any  non-empty  path  component  (it  stops  at slashes).
use "**" to match anything, including slashes.


I can't test it out right now, but I think you should try this:

```
rsync -rP --include=**.mp3 /home/jonathan/Music
```

Or possibly
```
rsync -rP --include=**\.mp3 /home/jonathan/Music
```
I'm not sure if you need to escape the "."

For more details/options, look at the "Filter Rules" and "Include/Exclude Pattern Rules" sections of man rsync.

This link may also help:
[http://www.linbox.com/ucome.rvt/any/doc_distrib/rsync-2.4.6/index.html]("http://www.linbox.com/ucome.rvt/any/doc_distrib/rsync-2.4.6/index.html")

---

