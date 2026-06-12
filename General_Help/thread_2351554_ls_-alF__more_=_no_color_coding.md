---
title: "ls -alF | more = no color coding"
date: 2017-02-04
forum: General Help
---

### Post by stringtheory on 2017-02-04
Is there any way to sneak color-coding thru pipes into 'more' or 'less'?

ls -alF             == color coded
ls -alF | less    == monochrome

---

### Post by &amp;KyT$0P# on 2017-02-04
```
ls --color=always -alF | less -R
```

---

### Post by stringtheory on 2017-02-04
That worked. Thanks.

---

### Post by &amp;KyT$0P# on 2017-02-04
You're welcome!  :KS

---

### Post by Keith_Helms on 2017-02-04
I added the following function to the end of my .bashrc file to do what you wanted
```

lsless() {
    ls -Cw 160 --color "$@" | less -r
}


```

---

### Post by vasa1 on 2017-02-04
> **stringtheory said:**
> That worked. Thanks.
Hi, the next time you want to mark your thread [SOLVED], please go to the top of the thread and use the "Thread Tools" as shown here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thanks!

---

