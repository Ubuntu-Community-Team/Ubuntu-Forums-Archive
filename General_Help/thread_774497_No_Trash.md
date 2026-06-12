---
title: "No Trash"
date: 2008-04-29
forum: General Help
---

### Post by Knad on 2008-04-29
Hello,

When I delete items ('Delete') key, they just disappear. They do not seem to be moving into any trash I can find. My panel applet says the trash is empty, and when i click to look in the folder, it is empty. Also when i go to ~/.Trash that is also empty:
[INDENT]adam@adam-laptop:~/.Trash$ cd ~/.Trash
[email]adam@adam-laptop:~/.Tras[/email]h$ ls
[email]adam@adam-laptop:~/.Tras[/email]]h$ 
[/INDENT]

Are my files just being deleted, or are they being moved somewhere else? Can you guys advise me, and how to get them to move to .Trash?

Thanks
Adam

OS: Hardy 8.04
GNOME: 2.22.1
Laptop: Dell Inspiron 6400
Installed the beta prior to release, all updates installed to current version.

---

### Post by XelNaga on 2008-04-29
type ///:trash in the address bar and see what happen :D

---

### Post by aheckler on 2008-04-29
That would be "trash:///"

---

### Post by Knad on 2008-04-29
Yeah I just noticed!

I had clicked the trash icon and seen the folder was empty, so I wrote the post.

When I was closing the windows i discovered it had loaded all of the items!

Silly mistake, didn't realise I had to give it a chance to load!

Still, my trash applet (AWN Stacks Trasher) is not changing its icon....odd

Thanks though :)

---

### Post by |{urse on 2008-04-29
try 

```

ln -s ~/.local/share/Trash/files/ ~/.Trash
```

as per this thread

[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1683&page=1&isLive=true]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1683&page=1&isLive=true")

!oh sorry didn't read your last post!

---

