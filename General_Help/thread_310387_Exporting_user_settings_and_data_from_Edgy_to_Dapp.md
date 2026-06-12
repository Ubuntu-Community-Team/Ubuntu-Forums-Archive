---
title: "Exporting user settings and data from Edgy to Dapper?"
date: 2006-12-01
forum: General Help
---

### Post by identitet5000 on 2006-12-01
Well, unfortunately, it seems that Dapper worked much better for me. 
So I'm planning to go back to Dapper, but - is there some way I can export my user settings, like Firefox history and bookmarks, Terminal settings, and so on, in one swift move?

---

### Post by bernied on 2006-12-01
almost swift...
All of your settings are in your home directory. If you try:
```
cd ~
ls -al
```...you should see a whole lot of files and directories that begin with a . that are normally not shown. You can also see these in your GUI file manager, if you tell it to show you hidden files (if I remember correctly). So you probably want to copy those files across to your Dapper install... Except that it is probably not that easy as some of them will be specific to the Edgy install. 

So be careful - make sure you backup any files in the destination directories before you overwrite them

I suspect that some GUI related files are links to files somewhere else (not in your home directory), again take care.

---

### Post by AndyCooll on 2006-12-01
Your user settings are stored in your home directory, so copying them on to a CD/USB stick will keep them. You can then copy them back once you've done a re-install.

You need to be aware that you might run into some issues however since with Edgy you are using different versions of software to Dapper. And certain settings maybe now require the version in Edgy. E.g. Firefox on Edgy is now version 2.0. You'll be alright copying the bookmarks, but not necessarily themes.

:cool:

---

