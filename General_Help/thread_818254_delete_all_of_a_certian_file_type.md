---
title: "delete all of a certian file type"
date: 2008-06-04
forum: General Help
---

### Post by onesojourner on 2008-06-04
I have some random (a few hundred) .flac files in various folders in my music directory. I would like delete all of them. How can I go about that? I am sure there is an easy way with terminal.

Ex.

music>
    folder>
      xxxxx.flac
    folder>
      xxxxx.flac

---

### Post by aquavitae on 2008-06-04
In a terminal:
```
cd [insert the folder name, e.g. ~/Music]
find ./ -iname '*.flac' -delete

```
Note that this will delete them, not move them to trash. You can move them instead, but I can't remember the command offhand. Check out 'man find' for more info.

---

### Post by drs305 on 2008-06-04
You can find all those files using:
Run the first command to see the files:
```
find /pathtofolder/*.flac
```

Use this command to delete them, with approval of each deletion:
```
find /pathtofolder/*.flac | xargs rm -i
```

Use this to just delete them without confirmation:
```
find /pathtofolder/*.flac | xargs rm
```

---

### Post by bingoUV on 2008-06-04
One simple way is,
```

rm music/*/*.flac

```

This will only delete flac files in a directory one level inside music. If there is a directory within a directory in music, this command will not delete flac files from inside it. You might like this.

---

### Post by aquavitae on 2008-06-04
I didn't realise you could use find in that abreviated form! I always use the -iname arg. What is 'xargs'? - I haven't seen it before.

---

### Post by drs305 on 2008-06-04
> **aquavitae said:**
> I didn't realise you could use find in that abreviated form! I always use the -iname arg. What is 'xargs'? - I haven't seen it before.

find is pretty powerful, i usually don't use switches but combine it with grep to limit what it 'finds'.

xargs basically takes the result(s) of the previous command and then executes the next command based on those results.

see: man xargs

also please mark this thread as solve when you have no more questions.

---

