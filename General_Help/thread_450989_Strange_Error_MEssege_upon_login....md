---
title: "Strange Error MEssege upon login..."
date: 2007-05-21
forum: General Help
---

### Post by FragMonkey on 2007-05-21
Alright so since yesterday I have been getting this strange error messege upon typing in my username and password and loging in. As I hit enter, I get this:

"[B]User's $HOME/.dmrc file is being ignored. This prevents
the defualt sessionand languge from being saved.
File should be owned by user and have 644
permissions. User's $HOME directory must be owned by
user and not writable by other users.[/B]"

Nothing seems to be affected though and I can download/delete files like normal.

I couldn't get a screenshot of it because I don't know if you can take screenshots while on the login screen.

Would anyone care to explain how to fix this?

---

### Post by vtel57 on 2007-05-21
Please open your Terminal program and type the following command:

```
$ ls -al /home
```

Post the output (result) of that command here.

Uh, just so you know, what you're doing here is listing (ls) all (-a) the contents of the /home directory along with the permissions (-l). This will tell me why the system is warning you that you (as the user) don't seem to "own" your own home directory. Here's what mine looks like:

```
vtel57@ericsbane03:~$ ls -al /home
total 60
drwxr-xr-x  4 root   root    4096 2006-12-20 21:12 .
drwxr-xr-x 23 root   root    4096 2007-05-06 18:53 ..
drwxr-xr-x  2 root   root   49152 2006-12-20 19:50 lost+found
drwxr-xr-x 34 vtel57 vtel57  4096 2007-05-21 21:39 vtel57

```

---

### Post by FuzzySkat on 2007-05-24
I have the same problem. I was try to remove this file, change owner (chown), change privileges (cmod), but error don't disappear...

---

