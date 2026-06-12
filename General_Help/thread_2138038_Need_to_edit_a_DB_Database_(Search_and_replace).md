---
title: "Need to edit a DB Database (Search and replace)"
date: 2013-04-22
forum: General Help
---

### Post by GameX2 on 2013-04-22
Hi,


I would like to edit a DB database.  In fact, the database where Clementine Player store the songs settings, such as play count.  The only program I managed to use to edit it was actually a Firefox extension called "SQLite Manager".  It work well, but lack a functionality I'm looking for: Search and replace.

The thing is, I want to move my Music folder out of my Windows partition, and put it on a blank partition instead (I plan on keeping my personal files out of my Windows 7 partition, now).  But moving the folder is quite a bad idea, since it erase all the play counts of the songs!  I had to restore a backup of the previous file. XD

Now, if only I could edit the database with a "Search and Replace"...  In the DB file, all the songs have absolutes pathnames pointing to sda3, and I want to change the path to sda8 instead.

Apparently, LibreOffice Base won't open the file.

Any help?
Thank you!

---

### Post by nonamedotc on 2013-04-22
Perhaps this? - [http://sourceforge.net/projects/sqlitebrowser/](http://sourceforge.net/projects/sqlitebrowser/)

The last commit to this project was in April 2012 - so I would say not too bad. You could give it a whirl ...

---

### Post by papibe on 2013-04-22
Hi GameX2.

Both of these GUI applications are available on the Software Center:
[LIST]
[*]SQLite database browser, and
[*]Sqliteman.
[/LIST]
If you are using 12.04, I'd recommend Sqliteman, as the other one has some issues.

Regards.

---

### Post by GameX2 on 2013-04-22
Thanks.

Should I absolutely create an SQL querie?  Sorry, I can't seem to find an option that would simply do a "Search and Replace" within all the database tables.. :/

---

### Post by papibe on 2013-04-22
AFAIK, yes. 

Probably you need to run an UPDATE. For instance:
```
UPDATE table SET field = REPLACE( field ,'old_string, 'new_string');
```
Where 'field' is the name of the column you want to replace in 'table'.

Let us know how it goes.
Regards.

---

### Post by SeijiSensei on 2013-04-23
If that syntax doesn't work, try

```
UPDATE table SET field='new_value' WHERE field='old_value';
```

---

### Post by GameX2 on 2013-04-28
Thank you.

Doing this did the trick.  The paths are replaced:
```
UPDATE subdirectories SET path = REPLACE( path ,'/media/sda3/Users/Admin/Music','/media/DATA/Musique');
```

However, for some weird reasons, Clementine can now access the library in the right directory, but when it start playing a song, it just skip it. :S  Something must have broke.

I should try an alternative way, I know I can modify the playcount manually in the database without breaking it.
How could I export the whole "playcount" and "skipcount" column (to a text file?), then import it in a new blank database (That will be created by Clementine) ?

Thank you!

EDIT: I can select what I want with this: SELECT title,playcount,skipcount FROM songs but how can I export it, then import it in the blank database (Overwriting the content of the columns, which are 0 everywhere) ?

---

