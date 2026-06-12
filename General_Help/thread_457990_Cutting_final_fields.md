---
title: "Cutting final fields"
date: 2007-05-29
forum: General Help
---

### Post by UncleB on 2007-05-29
Hello all,

I'm looking to script something that will capture the final field of a path.

eg. /home/user/Desktop/Folder/Filename

I would like to use cut to get at the final field: 'Filename'.

In that example I would use cut with -d and -f specified to get it. However I don't know that the path will always be the same number of slashes.

So is there a way to qualify cut that will take the last field. Or is there another command like a kind of tail cut?

Thanks for any help.

---

### Post by fanatik on 2007-05-29
use awk:

```
james@maple:~/backup/Work/Docs$ echo $PWD
/home/james/backup/Work/Docs
james@maple:~/backup/Work/Docs$ echo $PWD |  awk -F/ '{print $NF}'
Docs
```

:)

---

### Post by UncleB on 2007-05-29
Perfect given the problem's description.

What I didn't say is that the path's will always be volumes or folders with a trailing slash.

It's actually an OSX script that involves the user dragging volumes from the Finder into the Terminal. This always results in the trailing slash.

With a little fiddling I have it working so:

TRG='/Volumes/NAME/'; echo $TRG |  awk -F/ '{print $(NF-1)}'
NAME

Thanks for that fanatik!

---

