---
title: "How to change directory to filesystem folder (ex. folder etc)"
date: 2012-10-23
forum: General Help
---

### Post by linuxvstheworld on 2012-10-23
I want to travel in the file system (were the dangerous things are) via command line, and with normal directories you'd just do cd and then the directory, so is there a way to go to file system with a command like that?

---

### Post by Cheesemill on 2012-10-23
Just use the cd command as you normally would, for example:
```
cd /
cd etc
```

---

### Post by Stonecold1995 on 2012-10-23
What do you mean?  Like, to change to a directory in root?  Then you'd do something like this:
```
cd /usr
```

If the filesystem is mounted, then you can move *across* filesystems the same way you move *within* filesystems.

---

### Post by bab1 on 2012-10-23
> **Cheesemill said:**
> Just use the cd command as you normally would, for example:
```
cd /
cd etc
```

@linuxvstheworld  The above is a glimpse at both relative and absolute paths.  Since everything starts at / you can always change to any directory with ```
cd /path/to/any/directory
```...or you can use relative addressing (this is relative to what your current working directory is (pwd).  So it you are at your home dir (pwd=/home/<your_user> you could just do this to get to /etc> cd /etc...if you wanted to go to <somedir> in you home dir you can either do ```
cd <somedir>
```...or ```
cd /home/<your_user>/<somedir>
```

---

### Post by linuxvstheworld on 2012-10-23
> **Cheesemill said:**
> Just use the cd command as you normally would, for example:
```
cd /
cd etc
```

"Cheesemill saves the day once more!" Thanks again.......

---

