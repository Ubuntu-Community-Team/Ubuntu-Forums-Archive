---
title: "Directory and sub directory listing"
date: 2017-04-06
forum: General Help
---

### Post by raleigh3 on 2017-04-06
Can I get a directory listing of everything below root ?

I only need the dirs and subdirs and not individual file names.

I figured that it would be useful in case my system gets corrupted.

---

### Post by Dennis N on 2017-04-06
Check out the utility called **tree**. It may meet your needs. See its man page for output options.

---

### Post by TheFu on 2017-04-06
$ find / -type d -ls
or
$ ls -lR /

But if you are worried about corruption, you'll need a backup.  Versioned backups are pretty easy these days. I have 60-120 days of versioned backups for my systems. The higher the risk for a system, the more versions are kept.  It is really efficient on storage and backup times too. Most days, the next version only takes 2-4 minutes per system.

$ tree -d can work too, but it doesn't show all the important file/directory metadata like owners, group and permissions. In a multi-user system like Linux, that data is absolutely critical.

But you still need backups.

---

### Post by raleigh3 on 2017-04-06
I tried those with sudo from root but I get permission denied.

sudo ls -lR > DIRS.txt
bash: DIRS.txt: Permission denied

Thanks Dennis.

I will try tree.

---

### Post by steeldriver on 2017-04-06
I don't really see how it would help in the case that your system becomes corrupted, but you would probably want to exclude "ephemerals" such as the /dev, /proc, /sys directories

```

sudo find / \( -path /dev -o -path /proc -o -path /run -o -path /sys \) -prune -o -type d > DIRS.txt

```

If you want to run it from the root directory then the issue (as with your attempted `ls` command) is that the redirection to DIRS.txt will also need root permission there - there are several ways round that, I'd suggest

```

sudo find / \( -path /dev -o -path /proc -o -path /run -o -path /sys \) -prune -o -type d | sudo tee DIRS.txt

```

---

### Post by Dennis N on 2017-04-06
> tree -d can work too, but it doesn't show all the important file/directory metadata like owners, group and permissions. In a multi-user system like Linux, that data is absolutely critical.

You could include owner, group and permissions with additional options:

**tree -d -p -u -g**

would do it (here, limiting to directories only).

Best to study the options from the man page, and experiment. Another useful thing you can do is save the output to a file:

**tree -d > tree-output.txt**

---

### Post by TheFu on 2017-04-06
Try

$ sudo ls -lR > /tmp/DIRS.txt

The cwd doesn't get elevated permissions for your output file.  Put it somewhere that your normal userid can write - /tmp/ is a good place for that.

Might be worth gaining a little understanding of file and directory permissions.  Takes about 45 minutes of real effort to learn, then stuff like this won't get in the way ever again.  I don't know of any shortcut for this learning.

---

### Post by raleigh3 on 2017-04-07
Does not work.

> **TheFu said:**
> Try

$ sudo ls -lR > /tmp/DIRS.txt

The cwd doesn't get elevated permissions for your output file.  Put it somewhere that your normal userid can write - /tmp/ is a good place for that.

Might be worth gaining a little understanding of file and directory permissions.  Takes about 45 minutes of real effort to learn, then stuff like this won't get in the way ever again.  I don't know of any shortcut for this learning.

I have spent many hours of effort.

Please keep it simple for me.

I am familiar with dir permissions.

What is userid ?

I ask that you break it down into individual steps.

I appreciate your help. :-)

---

