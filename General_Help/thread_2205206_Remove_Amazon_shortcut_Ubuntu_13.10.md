---
title: "Remove Amazon shortcut Ubuntu 13.10"
date: 2014-02-12
forum: General Help
---

### Post by tomstewart on 2014-02-12
Hi guys,

I've recently done a clean install of Ubuntu 13.10. I was annoyed by Amazon ads in my Unity search results, and was able to remove them, along with removing Amazon from the launcher.

However, a shortcut to Amazon persists under "Applications" in my search results in Unity:

[ATTACH=CONFIG]250288[/ATTACH]

When you right click it you get:

[ATTACH=CONFIG]250289[/ATTACH]

If at any point you click it proper, or choose "Launch" from the image above, it opens Amazon.com in your browser:

[ATTACH=CONFIG]250290[/ATTACH]

I don't want Amazon to be part of my OS. Does anyone know how to get rid of this shortcut?

Thanks so much,

Tom.

---

### Post by tomstewart on 2014-02-13
No-one?

---

### Post by 3rdalbum on 2014-02-13
Delete it from /usr/share/applications/

---

### Post by tomstewart on 2014-02-14
Thanks, but even though I can see it in that folder I can't delete it. When I right click it, deleting isn't an option. The only real thing I can do with it is click on it, which opens Amazon.com...

---

### Post by ubudog on 2014-02-14
> **tomstewart said:**
> Thanks, but even though I can see it in that folder I can't delete it. When I right click it, deleting isn't an option. The only real thing I can do with it is click on it, which opens Amazon.com...

Most likely, you need to be root to delete it.

---

### Post by jim38 on 2014-02-14
And if you haven't done that before
Change directorys to were the file is
and do 'sudo rm <whatever the filename>
wiithout the "<>" :D

---

### Post by 3rdalbum on 2014-02-15
You can open a root file browser by opening the terminal and typing 'gksudo nautilus'. Then you can navigate that window to /usr/share/applications and delete the Amazon launcher.

Alternatively, you can open a terminal and type 'sudo rm ' and then drag the Amazon launcher file to the terminal.

---

