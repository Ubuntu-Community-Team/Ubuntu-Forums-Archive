---
title: "&quot;Sorry Ubuntu 22.04 has experienced an internal error&quot;"
date: 2024-02-03
forum: General Help
---

### Post by lisa_gibson on 2024-02-03
I've updated, restarted, even tried googling to see if anyone has had this exact problem but no can do. I screen shotted this recent "error" and not sure what it is about. Any help is great :D
[https://ibb.co/5WV9Wrq](https://ibb.co/5WV9Wrq)
 (im unable to embed the  pic  for some reason :( )
[IMG]https://ibb.co/5WV9Wrq[/IMG]
[IMG]https://ibb.co/5WV9Wrq[/IMG]

---

### Post by oldfred on 2024-02-03
Are you trying to install tracker from 20.04?
As you say you have 22.04, but error seems to be from 20.04?

Post this in code tags using # and Forum's advanced editor.
cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done

---

### Post by lisa_gibson on 2024-02-04
i'm not sure how to revert back to 20.04.  Is there a ppa or command line to do so? Thanks for the help :D

---

### Post by oldfred on 2024-02-04
No.

You typically reinstall & restore from backups.
But some applications when updated to new version may not work in old version. I had issues using same Firefox data. New version updated somehow & then old version would not open it. I had good backup, so not an issue.

---

### Post by deadflowr on 2024-02-04
Package version is correct for 22.04.
Tracker is a metadata database indexer and search tool. it's suppose to make searching for files and apps faster and more organized.
(That's the gist of what it is suppose to do)
It's part of the Gnome desktop that Ubuntu uses.

Does it crash often? Or was this a one-time thing?

If it crashes often the press send to report the issue to the bug squad.
If it only happened once press whichever you like.

I would guess it was a one-time thing as tracker is finicky.

I mean, you can run the desktop (mostly) fine without it.
See: [https://ubuntuforums.org/showthread.php?t=2488303&highlight=tracker]("https://ubuntuforums.org/showthread.php?t=2488303&highlight=tracker")

---

