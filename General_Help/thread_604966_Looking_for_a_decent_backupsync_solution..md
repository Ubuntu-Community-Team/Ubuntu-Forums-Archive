---
title: "Looking for a decent backup/sync solution."
date: 2007-11-06
forum: General Help
---

### Post by Ghostlove on 2007-11-06
I like to keep a copy of all my media files on an external hard drive. The music is easily replaceable but the 4,300-odd photographs and many, many personal videos all documenting the last two years of my son's life are irreplaceable.

Thus I backup regularly, using a terribly old-fashioned and inefficient method of copying all the folders I want to back up, and then pasting them into my shared hard drive, telling it to overwrite files of the same name, as this generally means I have an updated version of said file. I am just doing exactly that, plus all of my video and music files. As you can imagine, it takes FOREVER.

I have tried backup programs in the past, but what I really want is not to backup my data, just to keep the Pictures, Video and Music folders in my Home folder synchronised with the Pictures, Video and Music folders in my external hard drive.

Basically I'm looking for something where if I change a music album and add some photos, it automatically copies those specific things to the external drive. Otherwise when I go to back up I can't remember which bits I've added/changed, to my Home folder, so I always end up copying the whole lot over again which takes aaaaages.

Does such a magical tool exist, or am I living in a dream world? :confused:

---

### Post by Sunforge on 2007-11-06
If you just want to keep two folders in synch then your best option is RSYNC.

sync -avu --delete /path/to/your/folder/ /path/to/remote/folder

That will keep things pretty much in line.

Here's a reasonable article to get you started:

[http://www.enterprisenetworkingplanet.com/netos/article.php/10951_1573881_1](http://www.enterprisenetworkingplanet.com/netos/article.php/10951_1573881_1)

---

