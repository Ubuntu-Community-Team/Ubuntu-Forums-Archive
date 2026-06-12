---
title: "Document Folder Suddenly Became A Program"
date: 2007-01-06
forum: General Help
---

### Post by MDominic on 2007-01-06
OK...here's one I haven't been able to find any information on:
I have a document folder under "Documents" that today, for reasons unknown, has suddenly turned into a program.
The mime type is reading "application/octet-stream", and I am apparently not the owner, so I cannot change or do anything with this folder.  There's nothing in there I need, so I suppose I can delete it, but I'm just curious as to what would make it spontaneously change from a folder to a program.  
Any help?

---

### Post by tyl on 2007-01-06
While I can't peg what would cause a directory to assume the identity of an application, there should be a pretty straightforward way to regain control of the directory.

But should the situation arise that you need to fix it or it happens again, first drop into a terminal and punch out```
ls -l
```to see what is up with the permissions (use ```
whoami
``` or ```
id
``` to find out who you are to see if the ownership matches).  Should the ownership not match, do a quick
```

sudo chown username:username foldername

```
to restore your power over the directory.  Then you can fiddle with it as you like.

---

### Post by MDominic on 2007-01-08
Hmmm...this doesn't seem to be working.  Everything I try, I'm getting a "permission denied" message.  The properties tells me the owner is "-1".  I think the problem may stem from the fact that there is a space in the folder name.  Terminal cannot find it as a folder.
Suggestions, please?

---

