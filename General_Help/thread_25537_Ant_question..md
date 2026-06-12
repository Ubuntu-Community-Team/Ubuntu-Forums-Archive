---
title: "Ant question."
date: 2005-04-10
forum: General Help
---

### Post by Taoism on 2005-04-10
I am trying to figure out if I have ant installed on my system and if so, where it is.

Java is installed:

```

youngka@pandora:~$ java -version
java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)

```

I can see a listing for ant:

```

youngka@pandora:~$ ls -alR /usr/lib | grep ant$
-rw-r--r--    1 root root   183 2005-03-31 15:37 qt3-assistant
-rwxr-xr-x    1 root root   60344 2005-03-27 18:42 ant

```

I am assuming this is the (java) ant (make) program?

I have a couple of noob-ish questions.

First, how can I run a command that not only tells me if a file/directory exists, but also the exact path to that file/directory?  There are so many directories under /usr/lib that the above grep doesn't help me much in locating where the ant executable is.

Second, once I figure where the ant executable is, how do I add it permanently to the $PATH variable such that it is always in it even when I reboot the whole machine?

Any answers are appreciated!

Thanks in advance.

Cheers,
Keith.

---

### Post by edubarr on 2005-04-10
Use the find command, something like " find /usr/lib -iname 'ant' " will give you the full path to where the executable is. You can update your $PATH by editing a file called .bashrc on your home directory. You can create one if you don't have it there. To include the a new path to the $PATH list just include this line:

PATH=$PATH:/put/new/path/here

Close the terminal and re-open it and it should be good to go.

---

