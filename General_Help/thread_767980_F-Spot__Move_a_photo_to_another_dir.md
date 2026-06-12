---
title: "F-Spot:  Move a photo to another dir?"
date: 2008-04-26
forum: General Help
---

### Post by frup on 2008-04-26
I have just today begun using f-spot, I quite like it and it's a lot better than I expected. In the past I have just used plain folders and nautilus.

The trouble is that all my photo's had the wrong dates and times. I went through and used the adjust time feature and everything is great... Except that each photo is under it's old year/month/day folder hierarchy. 

How to I force F-spot to reorganise my photo's under their new year/month/days so that everything is organised properly? I know programs like iTunes have the ability to re-organise libraries in this way.

A final question is that in the event of me needing to format/upgrade my computer how would I export all the photo's with their tags etc? Do I use the export function and export to compressed archive?

Cheers.

---

### Post by tistria on 2008-05-07
I have the same issue.  I think you may have to update the database with the new path.  Try the instructions [here]("http://seanhodges.wordpress.com/2008/01/30/relocating-your-existing-f-spot-photo-store-eg-photos-to-pictures/").

I got the error ```
SQL error: no such column: directory_path

``` which either means the new version has different column names in the database, or I typed it wrong.

EDIT:  In my version of f-spot the column is called "uri"

---

### Post by fragos on 2008-05-07
F-Spots imposed folder and date storage was a real pain foe me. I use gthumb image viewer which gives me the freedom to file my way by topic and project. It also provides basic photo editing.

---

### Post by tistria on 2008-05-07
I use the tagging features of f-spot, which I have not found in gthumb.  

I got the database transfer to happen, to do so I had to use a slightly different command in sqlite3:
```
sqlite> update photos set directory_path = 'file///home/[username]/Pictures' || substr(directory_path, length('file:///home/[username]/Photos/'), length(directory_path)) where directory_path like 'file:///home/[username]/Photos/%';

```

---

### Post by frup on 2008-05-10
Well improved management of the directories and file locations would really make the program more attractive. In about 6 months I should have some spare money so I may post a bounty somewhere if it hasn't been implemented by 8.10 or the like.

---

### Post by ckoester on 2008-05-21
There is an [extension]("http://f-spot.org/Extensions") for F-Spot that allows you to change the directory path in the database.  However, it is currently unstable and does not inform you when the update is complete.

It would be nice if this were a built-in feature, but for now you'll have to try the extension or use the command-line method mentioned above.

Whatever you do, backup the database first!
```
cd ~/.gnome2/f-spot
cp photos.db photos.db.backup
```

---

### Post by q1u2i3z on 2008-05-30
will this command allow me to view my photos without opening f-spot? I cant find my photos don't know where they are stored!

---

### Post by fragos on 2008-05-30
> **q1u2i3z said:**
> will this command allow me to view my photos without opening f-spot? I cant find my photos don't know where they are stored!

Left clicking a file causes execution with the default application. When you right click any file you get a drop down menu. The 1st item opens with the default application and the 2nd "Open With" will give you a list of registerted applications for this file type. You may select from that list for this execution only. If you want to change the default application, select Properties on the bottom and then the "Open With" tab. Selecting a different application will make it the default for all files of this type.

---

### Post by Alcareru on 2010-11-24
> **tistria said:**
> Try the instructions [here]("http://seanhodges.wordpress.com/2008/01/30/relocating-your-existing-f-spot-photo-store-eg-photos-to-pictures/").

In case someone using a newer version of Ubuntu stumbles here.. the new location of the database is ~/.config/f-spot/photos.db (As per noted [here](http://art.ubuntuforums.org/showthread.php?t=1238482).)
> **tistria said:**
> ...
EDIT:  In my version of f-spot the column is called "uri"
Yes that's quite right and while were at it, as per the comments in the instructions, one should also do the same updating for photo_versions table as well.

P.S. In case you one ain't too pro with sql using sqliteman to edit the database might be easier. You still need to craft the statements, but it might be easier there than on the terminal. Also I would like to point out that it seems the urls are in the database on the form "file:///base/url/to/your/images/yyyy/mm/dd/" so it's probably wise to make sure you keep the file:/// part and the trailing / character in place. I'm not sure if things work if you don't.

---

### Post by philinux on 2010-11-24
Necromancy.

Thread closed.

---

