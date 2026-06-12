---
title: "Code to forcibly empty trash can?"
date: 2007-09-24
forum: General Help
---

### Post by nerojrnde on 2007-09-24
I have a whole lot of files in my trash that refuse to be deleted due to permissions..a lot of them say broken link etc.

Im curious if there is a way to delete everything from terminal..like a force delete.

Thanks for any help to come.

---

### Post by R.Bucky on 2007-09-24
Here it is```
sudo rm -r ~/.Trash/*
```

---

### Post by nerojrnde on 2007-09-24
cool, did the trick. thanks

---

### Post by brydonhunter on 2007-09-24
If you want to force the deletion of files, use ...

sudo rm -frd ~/.Trash/*

The 'f' forces the files to be deleted.
The 'r' is for recursive.
The 'd' is for directories.

---

### Post by xela321 on 2007-09-24
I tried the same thing but it didn't work.  My trash is showing a lot of .pid files and I can't seem to delete them.  Any ideas?

---

### Post by brydonhunter on 2007-09-25
These .pid files are most likely Process ID files that are created by some processes that are running on your system. Perhaps if you cat them you can find out which process created them.

That said, usually these files are created in your /var/run directory and not the .Trash directory. Did you manually delete these files from the /var/run directory?

Maybe you can try the following:

from the CLI, type:

sudo su -
cd /home/<enter username here>/.Trash
rm -f *pid

Let me know if it worked.

---

### Post by xela321 on 2007-09-25
When I go to my .Trash directory, it is empty (ls -a shows nothing)

However, my trash can icon is non-empty and when I open it, i see a lot of .pid files.

---

### Post by brydonhunter on 2007-09-25
Sounds like your .Trash is confused!

Have you tried restarting your X-Session (logout and log back in)?

Check the "properties" of the .Trash icon, perhaps something is wrong there.

Let me know what you find.

---

