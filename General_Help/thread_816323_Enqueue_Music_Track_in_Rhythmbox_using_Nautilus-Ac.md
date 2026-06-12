---
title: "Enqueue Music Track in Rhythmbox using Nautilus-Actions"
date: 2008-06-02
forum: General Help
---

### Post by vjkeito on 2008-06-02
can anyone tell me how to do this?

these settings don't appear to work...

---

### Post by ibuclaw on 2008-06-02
Can you post what it says? The image is too small for me to read.

[EDIT]
Using the forums attachments would be a better idea.
When you next post, scroll down and click on "**Manage Attachments**" in the "**Additional Options**" part of the post message page.

Regards
Iain

---

### Post by vjkeito on 2008-06-02
Didn't accidentally resized to wrong resolution on imageshack.

I've uploaded again using the attachments

cheers
keito

---

### Post by fickenbaisage on 2008-06-02
I haven't tried your command yet, but from your screenshot you seem to be missing a slash( / ) before usr/bin/rhythmbox-client. Why not try it first and see if it works?

EDIT 1:Also in the parameters section use this command: "--enqueue %d/%f"
EDIT 2: I got your script to work with my corrections mentioned above, albeit with one condition: the song must exist in your rhythmbox library.

---

### Post by ibuclaw on 2008-06-02
Thanks for that...

First try setting the path so it starts with a forward slash.
ie:
```
**/**usr/bin/rhythmbox-client
```

Regards
Iain

---

### Post by vjkeito on 2008-06-02
by adding the preceding /

and --enqueue %d/%f parameter, I can confirm this does indeed work!  thank you so much! ;)

---

### Post by fickenbaisage on 2008-06-02
> **vjkeito said:**
> still doesn't work.  with the preceeding /

any other ideas?

Look at my earlier post, I got it to work.

---

### Post by krippa on 2009-08-05
There is a good python script that works really well together with nautilus and rhythmbox. You can more information here:

[http://seemanta.net/myblog/?p=509]("http://seemanta.net/myblog/?p=509")

---

