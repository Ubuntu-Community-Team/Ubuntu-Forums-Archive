---
title: "backup software?"
date: 2005-05-01
forum: General Help
---

### Post by veritas366 on 2005-05-01
I'm looking for a good gui backup utility.  I don't think there is one for Linux and I'm a little surprised. It seems that the ability to set up a backup by browsing thru files and simply checking off the ones you want backed up would be easy for someone to create.  Or is there one?

So, until one of you brilliant people does this, I have another question about a different approach.  I know how to use the "tar" command to backup a file or even a list of files.  However, is there some way to have it simply update those items that have changed since the last backup?  That is what I was interested in.  I suppose I can backup my entire /home directory every time, but that seems wasteful.

---

### Post by ametade on 2005-05-01
Have you tried [Unison](http://www.cis.upenn.edu/~bcpierce/unison/)?

```
sudo apt-get install unison unison-gtk
```

---

### Post by veritas366 on 2005-05-02
Well, that's a start.  I'll try it.  I'm just a little surprised that something so easy to find in Windows...a GUI backup where you simply go through all your files and put check the boxes next to them for backup doesn't exist.  I know Linux users like their terminal, but that could come out to a LOT of files to type if you only need certain ones and not a whole directory.

---

### Post by nocturn on 2005-05-02
[QUOTE=veritas366]Well, that's a start.  I'll try it.  I'm just a little surprised that something so easy to find in Windows...a GUI backup where you simply go through all your files and put check the boxes next to them for backup doesn't exist.  I know Linux users like their terminal, but that could come out to a LOT of files to type if you only need certain ones and not a whole directory.[/QUOTE]

There are plenty of apps that do what you want (like Arkeia), but most are not free.

Bacula is great but does not have a GUI either, however the problem of selecting files is not so big.
You create filesets to back up, these can contain include and exclude directives.

So you can say, 'backup /home, but leave out all .tmp files and leave out /home/guest'.
The nice thing about programs like bacula is that the rest of it can run automaticly in the background.

---

