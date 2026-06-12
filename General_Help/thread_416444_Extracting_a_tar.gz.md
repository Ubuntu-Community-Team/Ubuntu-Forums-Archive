---
title: "Extracting a tar.gz"
date: 2007-04-21
forum: General Help
---

### Post by tictacman on 2007-04-21
I'm trying to extract the source code from a compressed file for dfast.  I've tried using different tools, downloaded the file repeatedly, no luck.  I've contacted the author who suggests I'm doing something wrong.  Can anyone else extract the source from official page?

[http://dfast.sourceforge.net/download.html](http://dfast.sourceforge.net/download.html)

---

### Post by heimo on 2007-04-21
Works fine here.
```
wget http://belnet.dl.sourceforge.net/sourceforge/dfast/wxdfast_0.6.0.tar.gz
tar xzvf wxdfast_0.6.0.tar.gz
```

If it doesn't work for you, check the format of the file:
```
file wxdfast_0.6.0.tar.gz 
```

> wxdfast_0.6.0.tar.gz: gzip compressed data, from Unix, last modified: Mon Mar 12 00:53:29 2007, max compression

---

### Post by tictacman on 2007-04-21
With archive manager gui tool I get


gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors


In the terminal

:~/Desktop$ tar -zxvf wxdfast_0.6.0.tar.gz 

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

---

### Post by heimo on 2007-04-21
My experience with that message is that when it says it's not in gzip format, the problem is that the file is not in gzip format. Try downloading using wget as in my previous post.

---

### Post by tictacman on 2007-04-21
Yep that's done the job.  Strange though, I never had any problems downloaded *.tar.gz files via the browser before.

---

### Post by heimo on 2007-04-21
> **tictacman said:**
> Yep that's done the job.  Strange though, I never had any problems downloaded *.tar.gz files via the browser before.

Happens to me all the time with Sourceforge mirrors. You most probably right-clicked [on the page you linked]("http://dfast.sourceforge.net/download.html"), and chose to "save link as". It seems to give you a .tar.gz file, but actually it gives you [a html page]("http://sourceforge.net/project/downloading.php?groupname=dfast&filename=wxdfast_0.6.0.tar.gz&use_mirror=heanet") of the page where you can download the actual file...

Yeah, it's a bit annoying, but when you know to watch for it (by looking at the browser status bar when hovering over a link), you can see when it's forwarding you to a mirror / download page and when to an actual file.

---

