---
title: "list directories"
date: 2007-07-08
forum: General Help
---

### Post by WilliamKB on 2007-07-08
This may have already been posted but I could find an answer on this forum.

I would like to list all the directories on a disk or under a directory but not the files. It would also be helpful if I could get the size of each directory.
I have tried 'ls -dR' but that doesn't seem to work. I have also looked at 'man ls' but can't seem to figure out the correct combination.

Thanks in advance for any help!!!!!!!!

---

### Post by kevinlyfellow on 2007-07-08
Maybe your looking for this?

```
du / | sort -nr | more #or less
```

It will organize folders by size of its contents

---

### Post by Mr. C. on 2007-07-08
```
find / -type d -ls
```

MrC

---

### Post by WilliamKB on 2007-07-08
Thanks kevinlyfellow and Mr. C.

Mr. C your way comes the closest for what I need.

Thanks again.

---

