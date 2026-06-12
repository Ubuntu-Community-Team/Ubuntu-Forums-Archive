---
title: "Is there a &quot;Search for Files&quot; that actually works?"
date: 2007-07-20
forum: General Help
---

### Post by OzzyFrank on 2007-07-20
Hi. I've come to realise that using Search within Nautilus is next to useless. I thought "Search for Files" was trouble free, since it would throw up more results than the other ever did, but I just noticed it is very flawed too. Like, it can't find any Flash (.swf) files, though I have a few of them in .opera (Opera's cache). I have told it to look through hidden files and folders, and have tried other things like running **gnome-search-tool** as root. I won't ask why this is so flawed, but will ask if there is any way to fix this? Or another search tool that can actually look through ALL my files?

---

### Post by picpak on 2007-07-20
catfish might work; install that and give that a try.

---

### Post by fragos on 2007-07-20
The best desktop search I've found is Google desktop.  It has recently been released for Linux.  When I installed it it took a few hours to scan my disk but it did that in the background my computers performance wasn't effected when I ran other applications like firefox and writer.  Searches are lightning fast like the web search engine.  When I do a google web search in firefox it also checks my desktop for matches.  I'm also running the Google toolbar in firefox so that may play a role in integration of desktop and web.

---

### Post by xl_cheese on 2007-07-20
find . / -name "*.swf"

---

### Post by OzzyFrank on 2007-07-20
Thanks for that; I'll try catfish to see if it does better. I just tried searching through the Opera cache folder for files including the text** .swf **and I got results, mostly .svg files that must have had those characters in the underlying code or something... but not even one .swf was listed! Andi have made sure the case matches, and all... and searching through that hidden folder seems to be no problem, as i at least got results that time... so what is going on?

[EDIT] Oh, and thanks for the Google and command line tips guys. Will try Google, as I prefer a GUI so I can drag/drop or "open folder" to copy/move/delete/whatever the files. Just using the **find** command now (thanks!) and it is giving me results... complaining about lack of privileges to search system folders, but right off it found all the .swf files in Opera's cache. I'll definitely make a launcher for that command and use it to make sure I'm not missing out on anything.

---

### Post by yorkie on 2007-07-20
When you click on places then search for files  when window opens make sure that
 look in folder points to your linux partition .
note when searching for files you can just put file extension in ie .sw  it will display all of your flash files can`t see any reason to download another search program.

---

### Post by OzzyFrank on 2007-07-20
Hi, and thanks, but I'm not that much of a beginnner, hehe... yes, it is definitely pointing to the right partition, and I point to Filesystem, my user folder, the actual ~/.opera/cache4 folder... telling you now, there ARE swf files there, but search just aint finding them! The **find** command did no probs, but search just gave me other file types when I specified to look inside files for the text, not just in names. This is weird, and annoying, hehehe.

---

### Post by yorkie on 2007-07-20
I don`t know why doing search for files is not working for I use opera and i find .swf files ok another way to try is   places  Home folder view check hidden files open opera folder then open cache4 folder then go to menu click on go then search for files type .swf  then enter your files wil be displayed

---

### Post by fragos on 2007-07-21
If you're only searching file names and will use the command line, try "locate".  Locate is instantanious since it searches a name index built once a day.  If you want to find a new file you need to run "updatedb" which can take a while depending on how many files are on your disk.

---

### Post by OzzyFrank on 2007-07-21
> **yorkie said:**
> I don`t know why doing search for files is not working for I use opera and i find .swf files ok another way to try is   places  Home folder view check hidden files open opera folder then open cache4 folder then go to menu click on go then search for files type .swf  then enter your files wil be displayed

Been there, done that, ain't happening. I can't see any logical reason why this is occurring.

---

### Post by xl_cheese on 2007-07-21
> **OzzyFrank said:**
> Thanks for that; I'll try catfish to see if it does better. I just tried searching through the Opera cache folder for files including the text** .swf **and I got results, mostly .svg files that must have had those characters in the underlying code or something... but not even one .swf was listed! Andi have made sure the case matches, and all... and searching through that hidden folder seems to be no problem, as i at least got results that time... so what is going on?

[EDIT] Oh, and thanks for the Google and command line tips guys. Will try Google, as I prefer a GUI so I can drag/drop or "open folder" to copy/move/delete/whatever the files. Just using the **find** command now (thanks!) and it is giving me results... complaining about lack of privileges to search system folders, but right off it found all the .swf files in Opera's cache. I'll definitely make a launcher for that command and use it to make sure I'm not missing out on anything.

sorry, you need to add sudo to the beginning of that command.  

sudo find . / -name "*.svg"

---

