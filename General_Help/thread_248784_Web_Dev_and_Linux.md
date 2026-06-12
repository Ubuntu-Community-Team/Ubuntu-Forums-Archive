---
title: "Web Dev and Linux"
date: 2006-09-01
forum: General Help
---

### Post by cbrack on 2006-09-01
Hi all,

I'm wondering if there is a web editor for linux out there that has the capabilities to connect to a server in a side-panel.  A good example of what I'm looking for would be like the ftp server connections in the file browser within Dreamweaver.

Does anyone know if quanta or bluefish have plugins somewhere that can do this?  If not, I'm considering developing one, because I think the linux web development programs need it.  

Hopefully once I get this problem solved I won't have to run VMWare all the time :(. Boo windows.

Anyways, any help is appreciated.  Let me know if there are other options to achieve the same effect as well.

Regards,

Chris

---

### Post by ayoli on 2006-09-01
you may try [nvu]("http://www.nvu.com") which is available via apt-get: 
```
sudo apt-get install nvu
```
regards.

---

### Post by cbrack on 2006-09-01
Does Nvu have the ability to connect to a remote server via ftp?

---

### Post by ayoli on 2006-09-02
yep in a side pane on the left you have a button 'Edit Sites' which opens a window where you can set the ftp server where to publish your pages.

---

### Post by cbrack on 2006-09-02
ah now i remember why i didn't use nvu... it didn't have PHP support.

Is there a plugin or anything for php work?

PS: i like the site manager.  didn't see that before.  I wonder why the other editors don't have it too?

Thanks,

Chris

---

### Post by ayoli on 2006-09-02
maybe an extension (like firefox extensions), but i don't know.
btw, for php dev i used eclipse with [phpeclipse]("http://www.phpeclipse.de/tiki-view_articles.php") plugin, and [fireftp]("https://addons.mozilla.org/firefox/684/") extension for firefox as ftp client to upload files.

---

