---
title: "Firefox"
date: 2007-01-16
forum: General Help
---

### Post by will61 on 2007-01-16
I'm rather new to Ubuntu I've only been using it for about three months 
I'm trying to set it up so that I'm not so dependant on MSwindows

My question is the following;
Could anyone tell me Where the folder is that firefox stores it's bookmarks in ?

I would like to import all my favorites from internet explorer I assume firefox has a folder for bookmarks although I've searched my Ubuntu filesystem with the key word's "bookmarks" and "firefox" and both searches came up blank 

Assuming they are stored in a folder then it should be easy to just cut and paste them in there if their stored in some sort of data file then it may become quite difficult to do

---

### Post by NeoLithium on 2007-01-16
I think firefox keeps them in 
/home/USERNAME/.mozilla/firefox

---

### Post by meng on 2007-01-16
Have you tried this?
Use IE to export bookmarks to some file.
In firefox, go to Bookmarks > Organize Bookmarks ... > File > Import ... and then import from the file you created with IE.

---

### Post by Sefrin on 2007-01-16
This may not be exactly what you're looking for but way back when I used IE and just installed Firefox for the first time, Firefox grabbed all my bookmarks from IE for me (all this was in Windows).  When I began using Ubuntu I exported my bookmarks from Windows Firefox to an html file on my NTFS drive that is mounted in Ubuntu.  Boot Ubuntu, open Firefox and then import the bookmarks from that html file.

---

### Post by will61 on 2007-01-16
Ok thanks for the replies, very much appreciated but it looks like there's no way to do this the simple way 

It seems firefox holds it's bookmarks in HTML format and not as individual links like explorer, and cross platform migration doesn't seem to be an option.

it looks like I'll have to edit "bookmarks.html" in  /home/user/.mozilla/firefox/scj6mpx6.default

---

