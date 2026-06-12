---
title: "scriptable bash way to see if any filesystem is mounted to more than one mountpoint?"
date: 2014-04-15
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-04-15
Is there any fairly direct bash scriptable way to either:

check to see if ANY filesystem is mounted to more than one mountpoint?

  or, failing that,

check to see if a PARTICULAR filesystem is?

Since there are several ways to get a list of mounted filesystems in the format of one system to a line with the /dev/sdLN or /dev/hdLN construction beginning the line a more general solution to the question:

How can I check if any 2 lines are the same up to the first space?

would be an effective solution but there may be other approaches.

I can certainly do this in a Rube Goldberg fashion - for each line get the part before the first space and then test the whole thing for the number of times that appears - but I'm wondering if there is something more direct.

Thanks for reading.

---

### Post by steeldriver on 2014-04-15
Not sure why you'd want to do this, but you could cut (or awk) the first whitespace separated field, then pipe the results to uniq -c ?

```

$ mount | cut -d' ' -f1 | sort | uniq -c
      1 //192.168.1.127/backup
      1 192.168.1.127:/c/home/steeldriver
      1 binfmt_misc
      1 devpts
      1 /dev/sda5
      1 /dev/sda6
      1 gvfs-fuse-daemon
      5 none
      1 proc
      1 rpc_pipefs
      1 sysfs
      1 tmpfs
      1 udev

```

If you want only the non-unique ones, you could add -d to the uniq

```

$ mount | cut -d' ' -f1 | sort | uniq -dc
      5 none

```

---

### Post by Dreamer Fithp Apprentice on 2014-04-16
Thanks, Steeldriver. That helped a lot.  I didn't know about uniq. Man uniq got me the rest of the way. This is a lot shorter than it would have been and it works:
```
mount -l |  grep -E '/dev/sd|/dev/hd' | cut -d' ' -f1 | sort | uniq --repeated
```It  returns the device name of a double mounted device in the /dev/(s or h)dLN form and returns nothing if no partitions are mounted to more than one directory.

Illustration:```
me@ubuntu:~$ mount -l |  grep -E '/dev/sd|/dev/hd' | cut -d' ' -f1 | sort | uniq --repeated
me@ubuntu:~$ sudo mount /dev/sda8 /media/me/test
me@ubuntu:~$ mount -l |  grep -E '/dev/sd|/dev/hd' | cut -d' ' -f1 | sort | uniq --repeated
/dev/sda8
me@ubuntu:~$ sudo umount /media/me/test
me@ubuntu:~$ mount -l |  grep -E '/dev/sd|/dev/hd' | cut -d' ' -f1 | sort | uniq --repeated
me@ubuntu:~$ 
```
And that of course is exactly the kind of binary yes/no output I need to use it in a script.

Now as to why I'd want to do it:
To keep it short:
For reasons not germane, I sometimes have a partition mounted in more than one place.  Just take it as a given. I also have scripts that act on files in other partitions. Writing those can get real hairy if there is a possibility the same partition is mounted more than once. I can revise a lot of stuff and eliminate the possibility of there being multiple mounts, even in cases where a script terminated abnormally. I'll be doing some of that anyway, but it isn't a tiny project and it sure won't be done overnight. And/or I can anticipate every possible way I could have multoply mounted partitons and revise every existing script and write every new script in such a way that it can cope with any of those possibilities. And not miss any possibilities. Even if I'm good enough to do that in a manner that I could be confident that I hadn't missed anything, and I don't think I am, I sure couldn't do it quickly.

But what I CAN do quickly is put in every script that might be sensitive to this a prefatory bit of code that tests for multiple mountings and on finding one, branches to a read -p with an informative error message and exit.

Thanks much.

-----------
In between when I stared this and actually posted it (lot of interruptions here) I see you added a bit. -dc must be the same as --repeated. Cool.

---

### Post by steeldriver on 2014-04-16
Here's a possible alternative ... just because ...

```

awk '/\/dev\/[hs]d/ {a[$1]++}; END{for(d in a) if (a[d] > 1) print d}'

```

---

