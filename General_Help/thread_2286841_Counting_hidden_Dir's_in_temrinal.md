---
title: "Counting hidden Dir's in temrinal"
date: 2015-07-15
forum: General Help
---

### Post by cowboy.bebop on 2015-07-15
I managed to get a hidden file count using 
```

#: hiddenfilecnt=$(ls -A | egrep '^\.' | wc -l)

```

but I cant seem to get a hidden dir count using 
```

#: hiddendirecnt=$(ls -Ap */ | egrep '^\.' | wc -l)
#: hiddendirecnt=$(ls -p */ | egrep '^\.' | wc -l)
#: hiddendirecnt=$(ls */ | egrep '^\.' | wc -l)
#: hiddendirecnt=$(ls -Ap | egrep '^\.' | wc -l)
#: hiddendirecnt=$(ls -ap | egrep '^\.' | wc -l)


```

Please keep it simple for me, dont confuse me with find or code blocks =P

---

### Post by Lars Noodén on 2015-07-15
If you are using [ls](http://manpages.ubuntu.com/manpages/trusty/en/man1/ls.1.html) to find directories, then you'll also need to look for names ending in a slash to distinguish them from other types.

```

ls -Ap | egrep '^\.' | egrep '/$' | wc -l

```

However, it is really worth demystifying [find](http://manpages.ubuntu.com/manpages/trusty/en/man1/find.1.html).  All the options you supply to 'find' are with an implied logical AND unless you explicitly specify otherwise.  Below they are all ANDs where the first line finds only directories, the second line finds only standard files and not anything else.

```

find /home/ubuntwha/ -maxdepth 1 -type d -name '.*'  | wc -l
find /home/ubuntwha/ -maxdepth 1 -type f -name '.*'  | wc -l

```

---

### Post by cowboy.bebop on 2015-07-15
Yeah, I kept searching online and people were ruling ```
#: find
``` over ```
#: ls
``` but hadn't found and answer. But since you suggested find, it actually works great ty so much!

---

