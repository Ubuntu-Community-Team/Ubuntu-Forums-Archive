---
title: "Rdiff-backup How to find deleted text"
date: 2016-02-22
forum: General Help
---

### Post by mikodo on 2016-02-22
Hi. 

I want to play with rdiff-backup in the future.

Suppose one accidentally deletes the file in directory/folder/file (foobar) from <source> and  wants to restore it from backups. These would do that:

```
$ cp -a destination/foobar source

$ rdiff-backup -r/foobar source
```

Question:

What if, only some *text in a file of foobar was deleted and one wants to bring it back from a delta that is not the most recent backup of foobar? I am asking because if the respective file in foobar has recent additions to it that, one also wants to save, one wouldn't want to just bring back an older delta that doesn't have the most recent additions in it. One would want the deleted *text and the most recent file.

Is the only way to determine which of the delta files would have that deleted *text in foobar is, to guess and bring different ones "following instructions below" on how to construct an earlier version of a file of foobar? One would want to move the original out of source first for safe keeping. Then, bring back the earlier foobar one wants to be brought back to source and check for the deleted *text and copy it somewhere when it is found. Delete the returned foobar file and bring back the original one just moved for safe keeping. Would that do it?

```
rdiff-backup --list-increments /destination/foobar 
```

Then, pick out a few numbered stamped deltas, and copy them each like this and examine them to find the *text, one wants to retrieve: 

 ```
rdiff-backup -r 7D destination/foobar source
```

Addendum:

I think I found the function provided to, compare one delta to what is in source <now> using the time-stamped deltas. 

from man rdiff-backup:

```
--compare-full-at-time time

              Compare a directory with the backup set at the given  time.   To
              compare regular files, the repository data will be copied in its
              entirety to the source side and compared byte by byte.  This  is
              the slowest but most complete compare option.


```

I'll test it, and see how it works. 

All in all, rdiff-backup looks to be a pretty cool app.

Thanks, for reading.

---

### Post by mikodo on 2016-02-23
A bump to see if anyone who hasn't seen this and reads it now, has any comments.

Thanks.

---

