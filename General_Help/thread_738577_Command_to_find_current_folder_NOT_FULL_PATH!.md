---
title: "Command to find current folder? NOT FULL PATH!"
date: 2008-03-28
forum: General Help
---

### Post by Gerlads Mod on 2008-03-28
Is there a command that finds what directory your in?
I don't mean the entire path like **pwd** does, I need something that just displays the current folders name.

Say I'm in /home/root/
**pwd** would output **/home/root**
But I need something that would just output **/root**

Is there such a command or something similar?

I checked the info and man pages of **pwd** and there is no option to make it display the current folder.

---

### Post by monraaf on 2008-03-28
basename `pwd`

---

### Post by ibuclaw on 2008-03-28
If you want spaces to be included in displaying it

ie:
> 
:~/$ basename `pwd`
:~/$ this        <--- this output has been truncated!!!

:~/$ pwd
:~/$ path/to/this folder has spaces            <----- This is what I expect to see.


Use this command.

```
 pwd | sed "s,^\(.*/\)\?\([^/]*\),\2," 
```

If that is too much for you to remember, you can store it in an executable text and save it in your **/usr/local/bin** directory.

be sure to include **#!/bin/bash** on the first line of the document.

and give it a memorable unique name such as **cwd** (stands for Current Working Directory)

---

### Post by monraaf on 2008-03-28
> **tinivole said:**
> If you want spaces to be included in displaying it

ie:


Use this command.

```
 pwd | sed "s,^\(.*/\)\?\([^/]*\),\2," 
```

Forgot about the space thing, but this should be good enough: **basename "`pwd`"**

---

### Post by Gerlads Mod on 2008-03-28
Oh my god thanks so much.

---

