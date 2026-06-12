---
title: "Can't 'sudo' /etc/sysctl.conf.."
date: 2015-11-21
forum: General Help
---

### Post by simba4 on 2015-11-21
Can't 'sudo' /etc/sysctl.conf..

Hi there,

I am trying to setup my Transmission uTP and UDP buffer according _[this instructions]("https://falkhusemann.de/blog/2012/07/transmission-utp-and-udp-buffer-optimizations/")._

The problem is that this file: /etc/sysctl.conf responds constantly with 'bash: /etc/sysctl.conf: Permission denied'

I also tried to edit it - Permission denied.
Also got in as an Administrator - same thing.

I wonder why..

James

---

### Post by QDR06VV9 on 2015-11-21
See if this helps, a little reading there but good solid information.
[http://ubuntuforums.org/showthread.php?t=1955589](http://ubuntuforums.org/showthread.php?t=1955589)

---

### Post by Lars Noodén on 2015-11-21
sysctl.conf is a configuration file and not a script.  So you edit it rather than run it.  You are missing which program to edit it with.  Try nano, which is launched by sudoedit:

```

sudoedit /etc/sysctl.conf

```

---

### Post by SlidingHorn on 2015-11-21
> **Lars Noodén said:**
> sysctl.conf is a configuration file and not a script.  So you edit it rather than run it.  You are missing which program to edit it with.  Try nano, which is launched by sudoedit:

```

sudoedit /etc/sysctl.conf

```

I would add that one would normally use nano by its actual name.  Getting in the habit of running sudoedit unnecessarily could be a recipe for disaster...

That being said, running via sudoedit or sudo nano would be the way to go here...

---

### Post by Lars Noodén on 2015-11-22
When files are owned by root, as is t the case with  /etc/sysctl.conf, 

```

$ ls -lh /etc/sysctl.conf 
-rw-r--r-- 1 root root 2.1K Apr  1  2013 /etc/sysctl.conf


```

then sudoedit is the safe way to edit them.  What sudoedit does is make a temporary copy of the file that the user can edit with normal permissions  Then it launches the designated editor, which is nano here by default but could be gedit or geany or anything else if you specify so in the $EDITOR environment variable or in /etc/sudoers itself.  After the file is edited, saved and the editor is exited, then the temporary file is used to replace the original with the same privileges as the original.  The main point is to have the editor run as the normal user.  That does two things.  It stops the editor from dropping root-owned files in the user's directories by mistake.  It prevents shell escapes to root access and other tricks.   Unfortunately sudoedit has been mostly overlooked in the Ubuntu tutorials.  

Yes, plain sudo with an editor is risky and an unsafe habit, especially when you are tuning sudo's configuration to a greater extent than the Ubuntu default of all-or-nothing.  But sudoedit is the safe way (if anything is safe) to go when editing files with root permissions.

---

