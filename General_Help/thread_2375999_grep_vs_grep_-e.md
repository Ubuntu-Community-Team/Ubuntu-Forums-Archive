---
title: "grep vs grep -e"
date: 2017-10-29
forum: General Help
---

### Post by linux.girl on 2017-10-29
Hi friends,

If I am searching a file for more than one word, what would be the difference between using two pipes, i.e. | grep word | grep word and using grep -e word -e word ?

Thanks!

---

### Post by jeremy31 on 2017-10-29
Use the egrep or grep -e option as using two pipes will find matches for word1 and then filter them for matches for word2
See the differences with a command I use ```
modprobe -c | grep -i 14e4 | grep 4311
```
```
modprobe -c | egrep -i '14e4|4311'
```

---

### Post by linux.girl on 2017-10-29
Thank you Jeremy31, so just to make sure I understood - If I use two pipes as in example 1 the second grep will only search the output of the first grep. But if I use the example 2 with the egrep, then it will search for both words in the whole file, correct?

---

### Post by jeremy31 on 2017-10-29
You understand correctly, using egrep or grep -e will find all instances of the word(s)

---

### Post by linux.girl on 2017-10-29
Many thanks! Can you help me in this other thread as well? [https://ubuntuforums.org/showthread.php?t=2376002&p=13704850#post13704850](https://ubuntuforums.org/showthread.php?t=2376002&p=13704850#post13704850)

---

