---
title: "Problem with python scripts"
date: 2020-07-18
forum: General Help
---

### Post by piotr953 on 2020-07-18
Hello
I can't run unkdz.py in terminal.
File is executable and run from file manager.
 unkdz.py -f V49020d_00.kdz -x don't work

---

### Post by Bashing-om on 2020-07-18
piotr953; Hekko - welcome to the forum.

Maybe your script calls the dropped version of "python" ?
In my use case in bash scripts I do declare explicitly to use "python3".
```

# Force specific Python version
PYTHON="python3"

```

[INDENT]my bit to try and help
[/INDENT]

---

### Post by Impavidus on 2020-07-19
Is this Ubuntu 20.04? Then Python 2 no longer gets installed. It's still customary to use python3 to mean Python 3 and python to mean Python 2. If you wish, you can install **python-is-python3** from the repositories, which will just create a symlink so that python points to python3. It will cause obscure errors if you still have software depending on Python 2.

If your code actually requires Python 2, you have to install that. It's still available, but not will be dropped in a (not so far) future release of Ubuntu.

---

### Post by piotr953 on 2020-07-23
Ubuntu 16.04
piotr@piotr-Ex:~$ python2
Python 2.7.12 (default, Jul 21 2020, 15:19:50) 
[GCC 5.4.0 20160609] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
Python 3.5.2 (default, Jul 17 2020, 14:04:10) 
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
Nothing about in ubuntu help
Tanks for advice:)

---

### Post by Impavidus on 2020-07-24
I didn't read carefully enough. In the screenshot in your first post, you use the command **pyton** where it should be **python**.

---

