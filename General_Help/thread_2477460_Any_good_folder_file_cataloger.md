---
title: "Any good folder file cataloger ?"
date: 2022-07-25
forum: General Help
---

### Post by aug7744 on 2022-07-25
Hello.
Have any good file and folder cataloger using GUI for Ubuntu ?
Thanks for your reply.

---

### Post by TheFu on 2022-07-26
> **aug7744 said:**
> Hello.
Have any good file and folder cataloger using GUI for Ubuntu ?
Thanks for your reply.

ls -lR
find .

If we stay with plan text, the 50 standard tools on every Unix-like OS are available for future processing.  I have some tools that maintain and search my media collections, for example. Those "tools" are really just tiny scripts, usually 1-5 lines, that do 1 thing really well.  That's part of the Unix philosophy.  "Do 1 thing, really well."

I don't know what a "file cataloger" is.  Care to list some that you know about?   Alternativeto.net has alternatives for different programs, so using that can look up similar programs on other platforms.  [https://alternativeto.net/software/data-crow/](https://alternativeto.net/software/data-crow/) is one.  Ah ... it looks like you want a collection manager.  I use a few, but most are web-servers, not desktop programs, because I wanted access to the information from all my devices.  
* ebooks - Calibre Web server.  There is a fat GUI too. I only use it when importing new books (epub/html/pdf/txt).
* Video/Movies/TV - Jellyfin   - For playback, I use either VLC (Android) or OSMC (projector/TV connected with r-pi) Jellyfin has a web interface for most things.
* Audiobooks - file system layout    {author}/{Series}/{Bk#}-{Title}/{Trk#}-{Title}   <---- then I use locate, mpd,  or my music catalog tool for access.
* Music - file system layout  {genre}/{artist}/Album}/{Trk#}-{Title}   <---- then I use locate, mpd,  or my music catalog tool for access.
* Other collectables ... I collect accurate diecast aircraft, all of 1 size, to help provide clear size comparisons.  Use a spreadsheet to track these with about 20 columns for each model. 
* Plane spotting DB - Separately, I have a photo gallery with photos of each and photos of the same aircraft from places around the world. We are a crazy group of aircraft lovers.  Given a tail number to almost any aircraft, I can find where it is now if it flew recently.  If it hasn't flown recently, where it was last seen. Because aircraft are very regulated, the entire history for an aircraft, owners, typical routes, are typically available. I don't keep those local, just the photos that I took personally.

For example, if you want a deep search tool, then something like **recoll** can be good.  It has a GUI and can be setup to index places you like. It is like having your own Google for storage on your network.  The first Index can take some time, but searches are immediate and daily indexing isn't anywhere near as long. Depending on the helper programs, metadata from different file types are available too, so if your files have properties in their headers, that can be searched too.  

There are lots of options. Just depends on your needs.

---

### Post by dragonfly41 on 2022-07-27
Recoll ???   Correction I see it mentioned above.

---

### Post by aug7744 on 2022-07-27
@TheFu

I only want an file cataloger with GUI to create an database about folders and files.
Not exactly need advanced details as video and audio tags or etc.
I will try Recoll :)
Have an nice week.

---

### Post by TheFu on 2022-07-28
But what do you want to know about the directories and files?  Folders are a Mac thing, not Unix.
Recoll is an indexer and searcher - like google.  We don't get to see inside the DB. We get to look for things.  Compared to 'locate', which knows all the names and locations of all files on a system, Recoll is overkill and bloated.  locate has been around since before I started with Unix about 3 decades ago. I bet there's a GUI layer for it, somewhere.  Hook that up to a system-wide key-accel and it will be like those Windows file lookers from 20 yrs ago.

I've never heard of any of these below:
* Google found something called Catfish.  [https://www.unixmen.com/catfish-graphical-front-end-find-locate-commands/](https://www.unixmen.com/catfish-graphical-front-end-find-locate-commands/)  
* If you use KDE, seems the default file manager, Krusader has connections into locate: [https://docs.kde.org/trunk5/en/krusader/krusader/locate.html](https://docs.kde.org/trunk5/en/krusader/krusader/locate.html)
* [https://www.fossmint.com/file-searching-tools-for-linux/](https://www.fossmint.com/file-searching-tools-for-linux/) has more general purpose options, I suppose, including a part about recoll.

Heck, my editor, vim, has a recursive file search capability. I barely use it.  locate is easier and works on both desktops and servers.  Since I have only 2 desktop installs and about 20 servers, guess which is more useful to me. ;)

Anyways, please report back on what you try, what you like, what you didn't like, so we can understand better.  We all work different. I'd like to see if what you are doing is better for my workflows too!

---

