---
title: "How to hide stuff?"
date: 2007-03-14
forum: General Help
---

### Post by mikeaguilar1 on 2007-03-14
If i have files in a folder that i want to hide. how do i do that?

---

### Post by bks on 2007-03-14
You could just bury it somewhere in the filesystem and name it something inconspicuous.

---

### Post by teaker1s on 2007-03-14
like this unhidden  ```
 myfilename
```
hidden                  ```
    .myfilename
```
notice dot before name

---

### Post by christhemonkey on 2007-03-14
Begin the title with a .
eg:
Rename a folder called barge to .barge or a file pr0n.avi to .pr0n.avi
Voila, hidden.

---

### Post by hikaricore on 2007-03-14
But it won't be very hidden that way.  A simple:

```
ls -a
```

Inside the directory in question will show all files hidden by this manner.  And with the function to show hidden in most linux graphical file managers, this is even easier.

If you want things to stay hidden and no one has root access but you, I suggest making a hidden folder that is only readable/writeable as root.

```

mkdir .mystuff
sudo chown root:root .mystuff
sudo chmod uga-rwx .mystuff

```

This way you have to use "su" or "sudo nautilus" to even access the thing.  And it remains hidden from unskilled users just the same, but now they won't be able to stumble upon it.

Not the most practical thing to do but much more secure than just hiding the files.

---

