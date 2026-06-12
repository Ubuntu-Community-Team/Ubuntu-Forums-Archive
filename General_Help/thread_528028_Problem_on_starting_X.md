---
title: "Problem on starting X"
date: 2007-08-17
forum: General Help
---

### Post by satimis on 2007-08-17
Hi folks,

Ubuntu 7.04 server amd64
Fluxbox


After running;
$ sudo chmod 664 -c /home/satimis/
Password:```

mode of `/home/satimis/' changed to 0664 (rw-rw-r--)

```
I can't start X by running;
$ startx

It hangs a while then displaying```

Xauth timeout in locking authority file //.serverauth.4609
Xauth timeout in locking authority file //.Xauthority
...

```

$ sudo find / -name .serverauth.4609
No printout

I must run;
$ sudo startx
to start X

re-run
# chmod 640 /home/satimis

# ls -l /home | grep satimis```

drw-r----- 11 satimis satimis 4096 2007-08-17 15:34 satimis

```
Can't solve the problem

Please advise.  TIA

satimis

---

### Post by jamvegan on 2007-08-17
In UNIX/Linux directory permissions, execute is required to access the directory.  A directory with no execute permission is inaccessible to cd to or to use in a path.  Thus, granting read permission on a directory without execute permission is nearly useless.  All that you'll be able to do is read the file names in the directory with ls.  You can, however, grant execute permission without granting read permission, in which case the directory can be used in a path, but cannot be listed with ls, which can sometimes provide a bit of security through obscurity.

So, I'd try changing the mode to 775 and see if that fixes your problem.

---

### Post by satimis on 2007-08-17
Hi jamvegan,


> 
So, I'd try changing the mode to 775 and see if that fixes your problem.
Whether to run;

# chmod -R 775 /home/satimis

Thanks


satimis

---

### Post by jamvegan on 2007-08-17
Did you use the -R option originally?  Your post indicates only that you used -c.  If you run this:
> # chmod -R 775 /home/satimis
it will make all files in the directory executable, which is probably not what you want.  Running it without the -R will make only the directory executable (and therefore accessible).

---

### Post by satimis on 2007-08-17
> **jamvegan said:**
> Did you use the -R option originally?  Your post indicates only that you used -c.  If you run this:

it will make all files in the directory executable, which is probably not what you want.  Running it without the -R will make only the directory executable (and therefore accessible).
Hi jamvegan,


# chmod 775 -c /home/satimis```

mode of `/home/satimis' changed to 0775 (rwxrwxr-x)

```

Exit X

$ startx```

Xauth timeout in locking authority file //.serverauth.3113
Xauth timeout in locking authority file //.Xauthority
Xauth timeout in locking authority file //.Xauthority
Xauth timeout in locking authority file //.Xauthority
Xauth timeout in locking authority file //.Xauthority

```
Finally X started (Fluxbox)

On Fluxbox
only 3 items found on menu, xterm, Restart, Exit

Started Xterm

$ firefox
Can't start

$ sudo firefox
Firefox started

Why I can't find ".serverauth.xxx" before start X?


satimis

---

### Post by jamvegan on 2007-08-17
Hi, satimis,

Could you post the output of the following?
$ ls -ld /home/satimis
$ ls -l /home/satimis/.Xauthority

When firefox fails to start, does it do so silently, or do you get a command not found message?

Also, have you tried completely logging out of your terminal session and logging back in?

jamvegan

---

### Post by satimis on 2007-08-17
Hi jamvegan,


Strangely after switching off this box several hours, it revives.  Now I can start X as satimis.  I did not do anything further after replying your posting.

What comes to my eyes is;

1)
Unable to start X as satimis:
After login, the command prompt is```

satimis@ubuntu:\$
```

2)
can start X as satimis:
After login the command prompt is```

satimis@ubuntu:~$

```

"\" and "~"


> 
Could you post the output of the following?
$ ls -ld /home/satimis
$ ls -l /home/satimis/.Xauthority

$ ls -ld /home/satimis/```

drwxrwxr-x 11 satimis satimis 4096 2007-08-18 08:06 /home/satimis/

```

$ ls -l /home/satimis/.Xauthority ```

-rw------- 1 satimis satimis 152 2007-07-27 10:23 /home/satimis/.Xauthority

```


> 
When firefox fails to start, does it do so silently, or do you get a command not found message?

Not silently.  There was a number ```

[xxxx]
Exit

then command prompt

```
Sorry I can't recall exactly


> 
Also, have you tried completely logging out of your terminal session and logging back in?

Yes, otherwise I can't test "startx"

But I haven't rebooted the PC.


remark: 
the problem re starting "nano" on another topic still remains.  Now I'll try to fix it.


B.R.
satimis

---

### Post by jamvegan on 2007-08-17
Hi, satimis,

> "\" and "~"

When your home directory was inaccessible, logging in defaulted to placing you in the root directory, but once you change the permissions back, logging in places you in your home directory (which "~" is a shortcut for).

Both sets of permissions that you posted look as they should.

So everything's resolved now, in terms of this thread?  Or can you still not start Firefox?

jamvegan

---

### Post by satimis on 2007-08-17
Hi jamvegan,


> 
When your home directory was inaccessible, logging in defaulted to placing you in the root directory, but once you change the permissions back, logging in places you in your home directory (which "~" is a shortcut for).

Both sets of permissions that you posted look as they should.

Noted with tks.


> 
So everything's resolved now, in terms of this thread?  Or can you still not start Firefox?

Firefox can start either on Xterm or on Fluxbox menu without problem.  Tks


satimis

---

