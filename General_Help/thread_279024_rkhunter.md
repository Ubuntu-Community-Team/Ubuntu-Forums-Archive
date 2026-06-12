---
title: "rkhunter"
date: 2006-10-17
forum: General Help
---

### Post by Compact on 2006-10-17
I have installed rkhunter and when I scan the computer with it, the following error is returned: 

```
WARNING, found:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)
```It is important? What it means?

---

### Post by evilghost on 2006-10-17
Normal, false-positive, ignore it.

---

### Post by pedja_portugalac on 2007-12-13
Tonight check result:

Warning: The file properties have changed:
[02:23:15]          File: /usr/bin/awk
[02:23:15]          Current hash: 7bd14d67ff98ae633f95ef985fa944c1a9904bf5
[02:23:15]          Stored hash : 1a77edf9273da7a55843f941002f480fbada42de

Warning: The file '/usr/bin/gawk' exists on the system, but it is not present in the rkhunter.dat file.

Somebody can explain what's going on?

---

### Post by NickD-NLUG on 2008-03-07
I've just had exactly the same error, did you find a solution to this issue... even if it was the revelation that in some strange way "awk" had been compromised?

Thanks.

---

### Post by NickD-NLUG on 2008-03-07
Sigh, I'm sorry for posting so rashly, I've looked at this for about a minute and think I've figured out what's happened.  ( My error is doubly compounded as I asked this question in another thread ).

Looking at the program in question, /usr/bin/awk, it's actually a symbolic link to /etc/alternatives/awk :

root@host:/usr/bin# ls -l awk
lrwxrwxrwx 1 root root 21 2007-03-06 06:13 awk -> /etc/alternatives/awk

This in turn in a symbolic link to /usr/bin/gawk

root@host:/usr/bin# ls -l /etc/alternatives/awk
lrwxrwxrwx 1 root root 13 2008-03-06 09:52 /etc/alternatives/awk -> /usr/bin/gawk

So that any program or user using the default "awk" program actually ends up using gawk.

Looking at the man page of rkhunter it uses "SHA-1" hashes by default, so I can use "sha1sum" to see the hashes that rkhunter uses of the relevant files in /usr/bin :

root@host:/usr/bin# sha1sum ./*awk*
7bd14d67ff98ae633f95ef985fa944c1a9904bf5  ./awk
7bd14d67ff98ae633f95ef985fa944c1a9904bf5  ./gawk
335d763a47b86f61ea957735829ffa1048f3fa8f  ./igawk
1a77edf9273da7a55843f941002f480fbada42de  ./mawk
7bd14d67ff98ae633f95ef985fa944c1a9904bf5  ./nawk
790d4a0fe7da96b3f4df4fc8a94f1d9d60eaf9e5  ./pgawk

gawk and awk have the same SHA-1 hash, because awk just points to gawk.  nawk points to /etc/alternatives/awk too, which is why that also has the same output.

Looking at the original error:

Warning: The file properties have changed:                                                                                                                                                     
         File: /usr/bin/awk                                                                                                                                                            
         Current hash: 7bd14d67ff98ae633f95ef985fa944c1a9904bf5                                                                                                                              
         Stored hash : 1a77edf9273da7a55843f941002f480fbada42de

You'll see that the old hash was 1a77edf..... and if you look at the sha1sum output above, that's the SHA-1 hash for mawk.

So what's happened if that for our systems the symbolic link for /etc/alternatives/awk used to point to /usr/bin/mawk, but something ( I don't know what ) changed that symbolic link to point to /usr/bin/gawk.  As /usr/bin/awk points to /etc/alternatives/awk, that means that the hash for /usr/bin/awk has changed.  However because of the symbolic links the reason for the change is hidden from rkhunter, so it reports that the actual program has changed.

Nothing to worry about, ignore the error *as long as you've got the hashes above*.

There... once I looked at it properly it took me longer to write this up than figure out what the problem was.... ;)

---

