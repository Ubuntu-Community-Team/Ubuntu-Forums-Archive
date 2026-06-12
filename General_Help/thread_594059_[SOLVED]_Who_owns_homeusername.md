---
title: "[SOLVED] Who owns /home/username?"
date: 2007-10-27
forum: General Help
---

### Post by rudeboyskunk on 2007-10-27
Ok, I did something to mess up ownership of /home/rudeboyskunk, and so every time I log in I get a message telling me that nothing from my session can be saved, and that $HOME should be owned by me (the user).  When I do a sudo nautilus in terminal and get a rooted nautilus window, I right click on /home/rudeboyskunk, go to permissions, but cannot choose my username (rudeboyskunk).  Instead the closest thing I have is rudeboyskunk - Samba Guest Account.  Should root be the user?

It also tells me some file is being ignored.  I can't remember which one though.  It says this is why it cannot save anything.

I'm afraid to change permission to root before somebody tells me that's what I'm supposed to do.

The command that screwed it up was  sudo chmod 0777 /home/rudeboyskunk, which I got from a crappy tutorial on samba.  Any way to undo all this and go back to happier times?

---

### Post by earobinson on 2007-10-27
[code]earobinson@MinusOne:/tmp/ubuntu$ cd /home
earobinson@MinusOne:/home$ ls -la
total 28
drwxr-xr-x  4 root       root        4096 2007-10-16 23:36 .
drwxr-xr-x 22 root       root        4096 2007-10-24 23:34 ..
drwxr-xr-x 48 earobinson earobinson  4096 2007-10-27 16:58 earobinson
drwx------  2 root       root       16384 2007-10-16 23:27 lost+found[/code[


to change the owner use the command chown

---

### Post by kebes on 2007-10-27
Your home folder should NOT be owned by root.

Your home folder should be owned by your username. Basically the home directory name and ownership should match. I'm assuming your username is "rudeboyskunk".

To fix it, open a terminal (Applications > Accessories > Terminal) and type this:
```
cd /home/
sudo chown rudeboyskunk:rudeboyskunk rudeboyskunk/
sudo chmod 740 rudeboyskunk/
```

That should fix it.

---

### Post by rudeboyskunk on 2007-10-27
Thanks so much!  Worked perfectly!

---

### Post by IagainstI on 2007-12-04
Thanks! Worked perfectly for me, as well!

---

