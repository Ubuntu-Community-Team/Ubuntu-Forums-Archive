---
title: "Add new user's documents from /home off different drive."
date: 2013-06-03
forum: General Help
---

### Post by 73ckn797 on 2013-06-03
I know how to add a new user to my 13.04 install. The trick is that I have moved their 12.04 install on a seperate drive from a different computer. I have it setup to dual boot into either drive. I would prefer to be able to use the document folder on the other drive due to space limitations on the 13.04 drive. What procedure can be performed to "mark" that other drive for the new users documents? The 12.04 install could be left alone and used as a backup system. Ownership privileges may have to be changed.

---

### Post by Lars Noodén on 2013-06-03
How do you have the second drive mounted?  One common way would be to have it mounted as /home  The big task is to make sure that the new user id's match the old drive or vice-versa.  *ls -lh* will show you the ownership, *ls -lhn* will show you the numerical ids.  It is those that have to match.  

If you have a directory /home/73ckn797 that came from the old system, you could change it to the new user id with [chown](http://manpages.ubuntu.com/manpages/raring/en/man1/chown.1.html)

```

sudo chown -R 73ckn797:73ckn797 /home/73ckn797

```

Again, the numeric ids have to match properly.

---

### Post by CatKiller on 2013-06-03
If you're still booting from both drives & don't want to share Home folders because of changes in settings and the like so you're only interested in the Documents folder you can symlink the one directory to the other. You'll need to make sure that the "new" user has appropriate permissions on the directory, but that's about it. Middle-click-and-drag and pick Link Here.

---

### Post by 73ckn797 on 2013-06-07
I was able to copy the documents to the main drive with room to spare so problem is solved and workable.

---

