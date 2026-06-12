---
title: "Using Grsync to back up home directory"
date: 2007-11-06
forum: General Help
---

### Post by michaelzap on 2007-11-06
I'm wondering what others have found to be the best practice for doing this. For example, how do I make sure that hidden files are included, and which files or directories are not really necessary to back up (.thumbnails, etc.). If anyone here uses an exclude file, can you please post it as an example?

Is there another tool for incremental backups that people prefer over grsync?

Thanks in advance for your replies.

---

### Post by fjgaude on 2007-11-06
Well, **Gsync** is good and I use it for backup. But going to my laptop I use **Unison** because it is two-way, if you know what I mean.

I don't use exclude, back everything up just in case.

The hidden files are auto backed by both programs. Both are solid, been around for a long time. Each have their place. And they both can do remote syncing.

---

### Post by michaelzap on 2007-11-06
Thanks for the reply. I may check out Unison when I need two-way syncing. It looks cool.

I think I figured out how to make Gsync do what I needed. I just added --exclude-from=".grsync/exclude" in the Additional Options field and then in my exclude file I just put each directory that I didn't want to backup on a separate line like so:
.Trash
.cache
.thumbnails
Downloads

For some reason it wasn't working when I referred to "~/.grsync/exclude" so that threw me at first, but getting rid of the home directory reference fixed it.

It backed up everything over the network so fast that I had to doublecheck all the files because it didn't seem posible!

---

### Post by meho_r on 2007-11-07
You may give Areca a try: [http://areca.sourceforge.net/](http://areca.sourceforge.net/)

---

