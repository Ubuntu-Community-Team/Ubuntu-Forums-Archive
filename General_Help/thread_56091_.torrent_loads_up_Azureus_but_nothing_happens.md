---
title: ".torrent loads up Azureus but nothing happens"
date: 2005-08-11
forum: General Help
---

### Post by Tristan9669 on 2005-08-11
When I click on a torrent file it loads up Azureus but it doesn't ask where to download and nothing downloads. To get it to work I have to load Azureus first or click on the torrent file then go to file>open torrent to actually load up the torrent and start downloading. Is there a way so that when you click on the torrent file it opens up Azureus and ask where to download and automatically start downloading, just like it does in windows, or is my Azureus just broken.

---

### Post by questionasker on 2005-08-12
[QUOTE=Tristan9669]When I click on a torrent file it loads up Azureus but it doesn't ask where to download and nothing downloads. To get it to work I have to load Azureus first or click on the torrent file then go to file>open torrent to actually load up the torrent and start downloading. Is there a way so that when you click on the torrent file it opens up Azureus and ask where to download and automatically start downloading, just like it does in windows, or is my Azureus just broken.[/QUOTE]
 i am 99% sure there is a way, although i have yet to figure it out...

see if anyone more knowledgable coems along to help... otherwise, its not THAT much of a pain...

---

### Post by Tristan9669 on 2005-08-13
Ok I found out how to get it working, Right click on the torrent file, go to properties then click on the open with tab, click add then use custom command and type /usr/bin/azureus then press add you can also do the same thing with firefox

---

### Post by questionasker on 2005-08-13
[QUOTE=Tristan9669]Ok I found out how to get it working, Right click on the torrent file, go to properties then click on the open with tab, click add then use custom command and type /usr/bin/azureus then press add you can also do the same thing with firefox[/QUOTE]
 glad you figured it out! :)

---

### Post by bvone21 on 2007-06-19
i added azureus to the custom command line for my ".torrent" 's.  I'm wondering if anyone knows how to get it to automatically launch the torrent file i clicked on?

right now it just opens up azureus...I'm sure there is an option like -somthin.  I'm trying to search for it but can't find any luck

edit: to clarify, azureus opens but you still need to "file>open torrent" to actually launch the torrent

---

### Post by badtlc on 2007-06-26
I have the same problem.  yet to find a cure.  It worked fine on 6.10.

---

### Post by Septicaemia on 2007-06-29
I'm also having the same problem. Does anybody know what the deal is?

---

### Post by volksman on 2007-07-22
To fix do this:

```
sudo nano /usr/bin/azureus
```

make sure it looks like this

> #!/bin/sh

/opt/azureus/azureus "$*"

Happy torrents... :)

---

