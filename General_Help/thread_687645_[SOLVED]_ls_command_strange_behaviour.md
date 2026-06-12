---
title: "[SOLVED] ls command: strange behaviour"
date: 2008-02-04
forum: General Help
---

### Post by Cannaregio on 2008-02-04
The solution to this problem of mine might be absolutely obvious, this inconsistency still beats me, though:

when I run

```
me@mybox:~$ ls /etc/*[COLOR="Blue"]ab[/COLOR]
```
I get  
```
/etc/anacrontab  /etc/blkid.tab  /etc/crontab  /etc/fstab  /etc/iftab  /etc/mtab
```

that is all nice and dandy, isn't it?
Yeah, [COLOR="Red"]BUT[/COLOR] when i run 

```
me@mybox:~$ ls /etc/*[COLOR="Blue"]re[/COLOR]
```
I get 
```
config.dpkg-old  config.old.0  license.vs.1.0-00  netmap.conf  pam.d  ssl  vm-list  vm-list-private
```

it's not so nice any more. What have those files to do with "[COLOR="Blue"]re[/COLOR]"?

Note that another, different, answer is given when files are missing:
```
ls /etc/*uu:  ----> No such file or directory
```

And this difference, in the example above between "[COLOR="Blue"]ab[/COLOR]" and "[COLOR="Blue"]re[/COLOR]", is what I don't understand. Probably something very simple I'm too doof to notice.
Any explanation?

---

### Post by lloyd_b on 2008-02-04
With the "ls" command, if the item specified is a directory, you'll get the contents of that directory (unless you explicitly tell it otherwise).  I'm guessing that you have a directory that matches that "*re" wildcard, and that is where those odd files are coming from.

Try "ls -d /etc/*re".  The "-d" flag will suppress "ls" from listing the contents of directories, and just give you the name of the directories themselves.

Lloyd B.

---

### Post by geirha on 2008-02-04
I'm guessing there's a directory ending with "re" in /etc, and it lists the content of that. The * isn't read by ls, it's read by the shell, and replaced by all files and directories that match the pattern. So if you have a directory with the two files "foo" and "bar", and run "ls *", then bash replaces the "*" so the command actually runs looks like "ls foo bar"

If it is indeed a directory ending with "re" in /etc, then try adding the -d option. That will make ls list the directory instead of its content.

```
ls -d /etc/*re
```

---

### Post by Cannaregio on 2008-02-04
```
me@mybox:/etc$ ls -d /etc/*re
/etc/vmware

me@mybox:/etc/vmware$ ls
config.dpkg-old  license.vs.1.0-00  pam.d  vm-list
config.old.0     netmap.conf        ssl    vm-list-private

```

Banging my head against the screen in shame.

---

