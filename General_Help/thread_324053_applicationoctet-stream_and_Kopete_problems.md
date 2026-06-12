---
title: "application/octet-stream and Kopete problems"
date: 2006-12-23
forum: General Help
---

### Post by Fragrag on 2006-12-23
As of recently, I've been having two very annoying problems. First of all, I've been getting error messages that do nothing as far as I know but do pop up occasionally:

> 
Could not find mime type
application/octet-stream


I've found a [solution]("http://www.linuxquestions.org/questions/showthread.php?t=133908") but that didn't work. I know that this problem is somehow related to file associations but I don't know how.

Second problem is possibly related to the first, the sound notifications in Kopete, like a beep when someone sends a message, have suddenly stopped. I checked the Notifications window and everything is as it should be. But when I try to preview the soundclip in Kopete itself, it plays nothing while with another player like XMMS it does play the sound. I've found other people having this problem but I haven't really found a solution.

EDIT; I've found a way to reproduce the first problem, basically just hovering my mouse over an image.

---

### Post by Fragrag on 2006-12-24
Sorry if this isn't allowed but I'd really like both problems fixed.

---

### Post by lucascr on 2007-02-08
For the first problem read 

[http://www.ubuntuforums.org/showthread.php?t=118485&highlight=Could+mime+type+application%2Foctet-stream]("http://www.ubuntuforums.org/showthread.php?t=118485&highlight=Could+mime+type+application%2Foctet-stream")

which basically suggests to remove the file ```
~/.kde/share/mimelnk/application/octet-stream.desktop
```
and this worked for me.

Luca

---

