---
title: "Recursive Delete throughout Multiple Directories"
date: 2013-06-19
forum: General Help
---

### Post by jll339 on 2013-06-19
Hey there,

So I want to delete all avgd files in all directories, hopefully with one command. I was curious if this would be acceptable (I'm very nervous about wiping out everything and not just the intended):

```
rm -ir *avgd
```

The intention is to delete interactively so it only deletes what I intended, and -r for recursive.
I'm not sure the wild care * works that way though, I've only used it on file types, not general words.

Is this the way, is there another way, or will I just have to go through each and every location manually?

**Stats:**
Ubuntu 13.04, 32-bit

Thanks!
jll339

---

### Post by VMC on 2013-06-19
This is a dangerous command and you should be nervous.  First off , back up your system. You could test it on a dummy dir's and files first.

---

### Post by jll339 on 2013-06-19
Good idea, thanks!

---

### Post by Lars Noodén on 2013-06-19
You could use find:

```

find . -name "*avgd" -exec echo rm {} \;

```

You can see the full list of options in the manual page for find.  But the above looks recursively in the current directory for any files ending in avgd and then does an 'echo' with the file name in the text.  Remove 'echo' once the output is what you want.

---

### Post by jll339 on 2013-06-19
The avgd files all end in different file types, though.

---

### Post by HermanAB on 2013-06-19
Yes, that command is OK.

What NOT to do:
NEVER use *. with rm, because * includes . meaning that you can then get .. which will back up one directory, which will then cause it to eventually recurse over the whole file system, which is usually not what you want.

---

### Post by Lars Noodén on 2013-06-19
> **jll339 said:**
> Nope... didn't work at all. Ok thanks unless anybody has any other ideas I guess I'll do it manually. Thanks again! 

The find command listed above won't actally delete anything until you modify it.  How to modify it should become more obvious once you get more familiar with how it works and what it does.

---

### Post by jll339 on 2013-06-19
> **Lars Noodén said:**
> The find command listed above won't actally delete anything until you modify it.  How to modify it should become more obvious once you get more familiar with how it works and what it does.

Hi thanks for your code from earlier, I actually made a test and tried it out on that. It worked perfectly! The not working comment I made and later changed was for another before I realized you had made a new post. Sorry!

I liked the echo part, it helped to clarify. Thanks again! I will use this method.

---

### Post by jll339 on 2013-06-19
Done! Thanks again! Quick question before I close this, I'm just curious as to why ```
locate avgd
``` will still show all these files and directories that don't exist anymore?

---

### Post by Lars Noodén on 2013-06-19
[locate](http://linux.die.net/man/1/locate) searches a database ([/var/lib/mlocate/mlocate.db](http://manpages.ubuntu.com/manpages/raring/en/man8/updatedb.8.html)) which is a snapshot of the system at the time the database was filled.  So if you move things around, install or uninstall things, the contents of the database will vary from what is really there.  

You should be able to force an update manually.

```

sudo updatedb

```

Otherwise, the database should get updated daily when your daily cronjobs get run.
What the database contains can be fine tuned in /etc/updatedb.conf

---

### Post by jll339 on 2013-06-20
WOW thank you so much, so useful! Thank you to everybody for all the help, everything worked out! :)

---

