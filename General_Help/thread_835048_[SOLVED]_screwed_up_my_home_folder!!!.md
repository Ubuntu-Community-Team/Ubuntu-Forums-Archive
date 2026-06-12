---
title: "[SOLVED] screwed up my home folder!!!"
date: 2008-06-20
forum: General Help
---

### Post by stldirty on 2008-06-20
ok i think i just botched my permissions in my home folder

all of the sudden my compiz started crapping out and when i went to reinstall it from git i realized that i was getting file permission errors and it wasn't letting me compile correctly.  so i started tinkering trying to set the correct permissions for my home folder and now i cant do anything.  i cant do a git clone.  i can't run autogen.sh.  nothing.  please someone help!!!!

---

### Post by ad_267 on 2008-06-20
Run this:

```
sudo chown -R your_username_here /home/your_username_here
```

That will make sure you own everything in your home directory.

You may have removed write permissions though if that doesn't work.

You can run ```
chmod -R u+w path/to/folder
``` to recursively give you write permission to a folder.

---

### Post by stldirty on 2008-06-20
> **ad_267 said:**
> Run this:

```
sudo chown -R your_username_here /home/your_username_here
```

That will make sure you own everything in your home directory.

You may have removed write permissions though if that doesn't work.

```
jarett@jarett-laptop:~/compiz/compiz$ sudo chown -R jarett /home/jarettsudo: cannot get working directory
[sudo] password for jarett:
chown: cannot access `/home/jarett/.gvfs': Permission denied

```

thats wut i get

---

### Post by Zorael on 2008-06-20
edit: Doh, well, you beat me to it.

Try doing it from a recovery session.

---

### Post by stldirty on 2008-06-20
> **Zorael said:**
> edit: Doh, well, you beat me to it.

Try doing it from a recovery session.

```
sudo chmod -R jarett:jarett ~
sudo: cannot get working directory
chmod: invalid mode: `jarett:jarett'
Try `chmod --help' for more information.

```

---

### Post by stldirty on 2008-06-20
oh ok

---

### Post by ad_267 on 2008-06-20
Yeah that thing about .gvfs is fine. You own everything in your home directory now so if you messed up that it's fixed. Now you'll have to see if you have write permission for things. You can use "ls -l" in the terminal and look down the left hand side to see the file permissions. Use that second command on a directory if you can't write to it.

---

### Post by Zorael on 2008-06-20
chown. :>

---

### Post by ad_267 on 2008-06-20
You can probably just recursively give write permissions to your home directory.

So if you've already run:
```
sudo chown -R your_username_here /home/your_username_here
```

You can run:
```
chmod -R u+r /home/your_username_here
chmod -R u+w /home/your_username_here
```

(I can never remember the numbers to use for chmod, so I just do the +r then +w.)

---

### Post by stldirty on 2008-06-20
ok recovery mode worked.  as far as i can tell everything is fixed.  thanks for the extremely quick responses guys :D

---

