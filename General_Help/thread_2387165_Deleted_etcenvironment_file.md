---
title: "Deleted etc/environment file"
date: 2018-03-15
forum: General Help
---

### Post by rhhernandes on 2018-03-15
So, I was experiencing the same problem seen on this topic: [https://ubuntuforums.org/showthread.php?t=2387028](https://ubuntuforums.org/showthread.php?t=2387028)

I was checking for what might have happened and trying to apply the fixes I found, but I ended up accidentally deleting the etc/environment file.

Now, the system won't go beyond the login screen. The form to insert the password disappears, but not even the desktop background loads.

Is there any way to recover it?


Thanks!

---

### Post by TheFu on 2018-03-15
```
$ more /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```

So you can probobly just boot using a liveCD/DVD/Flash version of Ubuntu, then drop to a root shell, mount the / partition/LV, create the file and put that 1 line into it.  Permissions are root:root 644.

How does someone accidentally delete a file that is in /etc/?   Please don't say you are using a file browser with sudo!

---

### Post by rhhernandes on 2018-03-15
> **TheFu said:**
> ```
$ more /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```

So you can probobly just boot using a liveCD/DVD/Flash version of Ubuntu, then drop to a root shell, mount the / partition/LV, create the file and put that 1 line into it.  Permissions are root:root 644.

Thanks! I'll try that tomorrow at work.


> **TheFu said:**
>  How does someone accidentally delete a file that is in /etc/?   Please don't say you are using a file browser with sudo!

Well, someone who clearly had even less clue what they were doing than I did suggested it.

---

### Post by TheFu on 2018-03-15
> **rhhernandes said:**
> Well, someone who clearly had even less clue what they were doing than I did suggested it.

Use **sudoedit** to edit files owned by root. It is the safest method.  Using sudo with most GUI programs is a bad idea and often has unintended repercussions.  It is possible to safely use sudo, provided the correct options are provided to change the HOME environment variable.  Best just to avoid it.

With sudoedit, you can use any editor you like. Just set the EDITOR environment variable to the program/file name for the editor on the system you want.

This doesn't help with file management stuff.  For that, I'm a shell/terminal-only guy.

Of course, others might have different opinions about all this.

---

