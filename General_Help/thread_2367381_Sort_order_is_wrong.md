---
title: "Sort order is wrong"
date: 2017-07-29
forum: General Help
---

### Post by zkab on 2017-07-29
I want to sort the time fields (pos. 1-16) in a file 'temp_sort' in ascending order.
The file 'temp_sort' contains lines with ping information.
My sort command is 'sort -n -k1.16 temp_sort > junkjunk'
However when I check the sorted file 'junkjunk' it is not correct ... below is a fraction from file 'junkjunk'.


2017-07-29 14:50:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms
2017-07-20 11:15:01      1 packets transmitted, 1 received, 0% packet loss, time 0ms

---

### Post by spjackson on 2017-07-31
Given the format of the date and time, simply
```

sort temp_sort > junkjunk

```
will do the right thing.

The reason your sort doesn't work is that -k1.16 doesn't mean positions 1 to 16, it means begin at position 16 in field 1 and continue to the end of the line. (See 'info sort' for more details.) Also, 1 to 16 ignores the seconds. Is that intentional?

---

### Post by zkab on 2017-08-01
Thanks - now it works ... but I added -n option
```
sort -n temp_sort > junkjunk
```

---

### Post by vasa1 on 2017-08-01
Then please mark the thread [SOLVED]: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

