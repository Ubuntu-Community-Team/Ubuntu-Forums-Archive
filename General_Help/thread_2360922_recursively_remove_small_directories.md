---
title: "recursively remove small directories"
date: 2017-05-09
forum: General Help
---

### Post by shoeleshunter78 on 2017-05-09
I need to delete all directories under 100M in size, but only one level (and no farther) down from home. For instance I need to remove a small directory ```
~/Movies/99M
``` while not removing ```
~/Movies/Keep/99M
```

thanks in advance

---

### Post by pruda on 2017-05-10
Hi, I belive something like this should work:
```
cd ~/Movies
find . -size +99M | grep --invert-match Keep > deletelist.txt
while read file ; do rm "$file" ; done < deletelist.txt
```
Be sure to check deletelist.txt if it really contains files you want to delete before executing the second line.

---

### Post by steeldriver on 2017-05-10
You need to be a little careful here - the *size *of a directory (as understood in the context of a find command) is not the same as the size occupied by the files in it

You probably want something based on the du command - I'd start by doing something like

```

du -0sm ~/Movies/*/ | while read -d '' -r size name; do ((size < 100)) && du -sm "$name"; done

```

Once you are convinced that it's identifying the appropriate directories, you can replace the **second **du command by an rm command

---

