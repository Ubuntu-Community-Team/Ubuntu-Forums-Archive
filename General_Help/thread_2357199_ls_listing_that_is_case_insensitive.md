---
title: "ls listing that is case insensitive"
date: 2017-03-30
forum: General Help
---

### Post by raleigh3 on 2017-03-30
Is there a way to get ls to be case-insensitive with it's listing ?

```
ls *.mp4
```

I would like to show both .mp4 and .MP4 files.

---

### Post by steeldriver on 2017-03-30
In bash, you can set the shell's nocaseglob option

```

shopt -s nocaseglob
ls *.mp4

```

To unset it again
```

shopt -u nocaseglob

```

---

### Post by raleigh3 on 2017-03-31
Thanks steeldriver.

---

### Post by vasa1 on 2017-03-31
@raleigh3, please read [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) :)

---

### Post by raleigh3 on 2017-03-31
I marked it solved.

---

