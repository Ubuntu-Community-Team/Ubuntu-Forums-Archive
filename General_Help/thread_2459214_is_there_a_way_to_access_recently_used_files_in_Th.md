---
title: "is there a way to access recently used files in Thunar"
date: 2021-03-13
forum: General Help
---

### Post by Ralph L on 2021-03-13
I would find it handy in Thunar to be able to display a list of recently used files that I could select from.  That way I wouldn't have to burrow deeply into my folders each time I want to access a file I used recently.  I found this suggestion in [https://unix.stackexchange.com/questions/392882/can-i-add-recent-items-view-to-thunar-bookmarks](https://unix.stackexchange.com/questions/392882/can-i-add-recent-items-view-to-thunar-bookmarks) .```


    Open ~/.config/gtk-3.0/bookmarks with your text editor.
    Add this line at the end: recent:/
    Save the file.
    Open thunar. There should be a recent bookmark on the side panel now

```  It works (sort of).  The file is opened with some made up name in the folder "recent:///.  If I make a change to the file, I can't save it to the original file.  So this really isn't of much use to me.
Is there any other feature or extension for Thunar that would display recently used files and let me modify and save them????
Any help appreciated....

---

### Post by TheFu on 2021-03-13
Have you considered using another file manager?  There must be 10 others. Just because you run XFCE, that doesn't mean you can't use different programs that aren't pre-installed. For example, caja has a search capability which will list files in less than a second.

The problem with "Recent files" is that only files touched using Thunar could be know to it, perhaps touched using Gnome programs.  Files touched by any other programs or methods would never show up without constantly running a notification tool, but then you'd see a bunch of Gnome dbs and settings in the list, probably not the data files you really want.  That would mean that some complexity to the filtering would be needed and everyone has different ideas about what should and should not be included.

I suppose you could run a task every 5 minutes or hour or day that looked for specific file types in locations you commonly use, then create a ~/Recent/ directory with symbolic links to the last 50 files with extensions you care about.  Then it wouldn't be tied to any GUI or file manager and you could dbl click to open the files.  Hummmm.  

I'm pretty certain that would work.  Heck, if the files were on the same file system, you could use hardlinks, but that would be a maintenance nightmare, since deleting the original wouldn't delete it from ~/Recents/ and the data would still use storage blocks.  Symlinks - definitely better.  Creating the links would be easy - say all the files in the last 7 days.  Cleaning them up could be brutal if a file was being opened through the symlink at the same instant.

I googled for a pre-built answer. Didn't see one.  I think it is 2 lines of script with a few setup commands first. I must be over simplifying it.
1) rm ~/Recent/*
2) mkdir ~/Recent ; cd ~/Recent/ ; find $HOME -type f -mtime -7 -a \( -iname \*ods -o -iname \*xls -o -iname \*pdf \)  -exec ln -s {} \;

I think that's it. Just add other extensions with a -o (or) and case-insensitive name pattern.  I think it is working.  Put that into a script and run it once a day.

---

### Post by dragonfly41 on 2021-03-13
I have looked at ways of indexing files scattered throughout my desktop.
I wrote a custom python file for that purpose.  e.g. by extension, by date accessed, by date changed etc.
But often I want to search for patterns inside files.
For the profile you cite I would try recoll indexing.

Ah! TheFu got there first as I was writing

---

### Post by TheFu on 2021-03-13
I use **recoll** too, but usually in batch searches based on file metadata. Recoll has a GUI, but I find it cumbersome to use ... like most file managers. ;)

Between **locate** and **recoll**, finding any files since the last daily index job was run is trivial and sub-second fast. Finding new files requires either using 'find' or re-running the indexing job on-demand.  Re-running locate isn't a big deal. Re-running a fresh recoll index can take some time.

I re-run the recollindex job daily at 4:10am via cron:
```
10 4 * * * export RECOLL_CONFDIR=/d/D2/recoll-index/recoll ; nice /usr/bin/recollindex
```

The index isn't tiny.
```
$ du -h /d/D2/recoll-index/
2.1G    /d/D2/recoll-index/
```
But there is about 20**TB** of files.
OTOH, the locate/mlocate DB on the same system is relatively small:
```
$ du -h /var/lib/mlocate/mlocate.db*
146M    /var/lib/mlocate/mlocate.db
```
That's just filenames.

---

### Post by Morbius1 on 2021-03-14
Are you using Thunar in Ubuntu or Xubuntu?

There appears to be a bug with recent:/// as a bookmark in thunar itself. But if you are using Xubuntu there is a panel applet called Places: Right-Click Panel > Add Item > Places.

When selected it will have an entry at the very bottom labeled: **Recent Documents** which will do what you want.

---

