---
title: "rm refuse ro remove folder! (nothing to do with the -R option)"
date: 2015-08-12
forum: General Help
---

### Post by goghvv on 2015-08-12
Hi.
I'm using Ubuntu on my personal laptop, and on my system, whenever I use rm on a file, it is gone. for good.
The problem is on my university server.
I am trying to delete a folder: environment/tests from my home directory. 
To my big surprise, when I use rm environment/tests (for some strange reason, rm does not require the -R option in order to delete a folder on the university server...), this is what I get:

```
u2 **** 114 $ rm environment/tests
/bin/mv: cannot move `environment/tests/' to `/u/stud/****/../TrashCan/****/tests': File exists
u2 **** 115 $
```
(the **** are replacement for my username)

So I tried to remove it from the Trash can, but realized it a recursive call... :D

```
u2 **** 157 : rm ~/../TrashCan/****/tests
/bin/mv: `/u/stud/****/../TrashCan/****/tests' and `/u/stud/****/../TrashCan/katoatz/tests' are the same file
u2 **** 158 : 
```

How can I delete this folder???
And what does mv has to do with it? (notice it is a /bin/mv error)

In fact, I want to completely empty the TrashCan!

Thanks in advance.

---

### Post by nerdtron on 2015-08-12
Can you try to empty the trash folder first? I'm not sure where is it the path of the trash folder on the server. Is that even ubuntu?

---

### Post by goghvv on 2015-08-12
No, it is not ubuntu on the server:

```
u2 **** 159 : uname -a
Linux u2 2.6.32-504.8.1.el6.x86_64 #1 SMP Wed Jan 28 21:11:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
u2 **** 160 :
```

The path to the Trash can is: "/u/stud/****/../TrashCan"

---

### Post by goghvv on 2015-08-12
Oops! sorry! I just realized I'm in Ubuntu forum... :D
Sorry for the bother.
I'll try somewhere else. Thanks anyway.

---

### Post by nerdtron on 2015-08-12
It seems like the rm command tries to move the files you want to delete to the trash folder. But the trash folder already contains some file with the same name. So try to empty the trash can first and then try to remove the files again.

---

### Post by btindie on 2015-08-12
Sounds like the 'rm' command might be aliased to something else. What's the output of 'type rm' ?

You should be able to delete it properly by using '/bin/rm' instead of just 'rm'.

If it's an alias, it may be defined in your ~/.bash_aliases file or it should be a system installed one with it being a university system that you're on, in /etc/profile.d/ ?

---

### Post by efflandt on 2015-08-12
Also I don't think you can rm (and know you cannot rmdir) a directory that is NOT empty unless you use -r or -R with rm to recursively remove everything in it.

---

### Post by Habitual on 2015-08-12
I have always used ```
rm -fr /path/to/directory
```

```
type rm
``` will show you what's what.

---

