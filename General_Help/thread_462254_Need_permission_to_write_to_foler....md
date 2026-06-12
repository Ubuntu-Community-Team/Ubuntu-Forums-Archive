---
title: "Need permission to write to foler..."
date: 2007-06-02
forum: General Help
---

### Post by kdarkentity on 2007-06-02
i want to move an image from my desktop to /user/share/pixmaps ...but i need permission

can i do this using the terminal?

---

### Post by intMain on 2007-06-02
> **kdarkentity said:**
> i want to move an image from my desktop to /user/share/pixmaps ...but i need permission

can i do this using the terminal?

try using "sudo mv /user/share/pixmaps/filename.ext <destination>/filename.ext"

---

### Post by aidanr on 2007-06-02
sudo cp ~/Desktop/image.png /usr/share/pixmaps/

roughly explained:

superuser do, copy, (~/ = home folder) source file, destination

edit:// beat to it, and of course move instead of copy :)

---

### Post by dfreer on 2007-06-02
actually, if it is from your desktop to /usr/share/pixmaps, you need to flip the command around. so:
```
sudo mv ~/Desktop/filename.ext /usr/share/pixmaps/**filename.ext**
```

ooops. I meant the second post, not the third one above me.
Yeah, cp = copy, mv = move, so depends on which one you want to do :D
The very last bit of the command, highlighted in **Bold**, is only really used if you want to change the filename when you move it. If you want it to keep the same name, you can simply do this:
```
sudo mv ~/Desktop/filename.ext /usr/share/pixmaps/
```

---

### Post by intMain on 2007-06-02
> **dfreer said:**
> actually, if it is from your desktop to /usr/share/pixmaps, you need to flip the command around. so:
```
sudo mv ~/Desktop/filename.ext /usr/share/pixmaps/filename.ext
```

ooops. I meant the second post, not the third one above me.
Yeah, cp = copy, mv = move, so depends on which one you want to do :D

oh, do this then. lol.  I haven't been using the terminal lately... shame on me.

---

### Post by dfreer on 2007-06-02
> **intMain said:**
> oh, do this then. lol.  I haven't been using the terminal lately... shame on me.

don't worry about it ;)

---

### Post by handydan918 on 2007-06-02
If this is likely to be an ongoing issue, another possibility is to change the permissions of the folder so you can write to it without sudo.
 something like:
sudo chmod 777 /pathname/filename.txt
the "777" will give completely unrestricted access to the file in question, so if that's not what you want to do, try "man chmod" for more options.

---

### Post by dfreer on 2007-06-02
> **handydan918 said:**
> If this is likely to be an ongoing issue, another possibility is to change the permissions of the folder so you can write to it without sudo.
 something like:
sudo chmod 777 /pathname/filename.txt
the "777" will give completely unrestricted access to the file in question, so if that's not what you want to do, try "man chmod" for more options.

Not always a good idea, but is *should* be ok with /usr/share/pixmaps, since it is just images. They have permissions generally for a good reason, it is far better to know how to copy/move files with sudo. 777 would allow the file/folder in question to not only allow all users to read/write, but execute as well. Only folders and files that actually need executed should be allowed to execute.

---

### Post by handydan918 on 2007-06-02
> **dfreer said:**
> Not always a good idea, but is *should* be ok with /usr/share/pixmaps, since it is just images. They have permissions generally for a good reason, it is far better to know how to copy/move files with sudo. 777 would allow the file/folder in question to not only allow all users to read/write, but execute as well. Only folders and files that actually need executed should be allowed to execute.

Good point. The 777 should not be used unless you know why you are doing it.Perhaps 666 would be better. Truth is, unless you do a little reading on permissions, it's easy to end up with files that are available to people they should not be available to. On most single user systems, this is not quite as critical, however.

---

### Post by Azakus on 2007-06-02
He'd have to do sudo chmod anyway, so using sudo cp would be better if he's only going to move a file once.

---

### Post by kdarkentity on 2007-06-02
all set guys...thx

---

### Post by satellite360 on 2007-06-02
```
sudo nautilus
``` is a handy one to know if you are not comfortable moving stuff around from the terminal.  Just be careful what you do!!!

---

### Post by dfreer on 2007-06-03
> **satellite360 said:**
> ```
sudo nautilus
``` is a handy one to know if you are not comfortable moving stuff around from the terminal.  Just be careful what you do!!!

I think this is good advice. It is pretty easy to mess stuff up in terminal simply with a typo, but it is hard to typo a mouse drag!

---

