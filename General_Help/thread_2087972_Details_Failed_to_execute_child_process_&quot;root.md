---
title: "Details: Failed to execute child process &quot;/root/Downloads/sh&quot; (No such file or direct"
date: 2012-11-25
forum: General Help
---

### Post by amitbedekar on 2012-11-25
Details: Failed to execute child process "/root/Downloads/sh" (No such file or directory)

I am getting above error while starting new program.
please help

---

### Post by mcduck on 2012-11-25
Could you explain in a bit more detail which program you are trying to start, and how?

---

### Post by amitbedekar on 2012-12-01
I am trying to execute JAVA based UNICENTA program as a root user.

But getting following error

There was an error launching the application.
Details: Failed to execute child process "/home/home/Downloads/sh" (No such file or directory)

---

### Post by rnerwein on 2012-12-01
> **amitbedekar said:**
> I am trying to execute JAVA based UNICENTA program as a root user.

But getting following error

There was an error launching the application.
Details: Failed to execute child process "/home/home/Downloads/sh" (No such file or directory)
i think your JAVA based UNICENTA program is a little confused.
have a look at your file system and i bet there is no directory /root/Downloads/sh either a directory /home/home/Downloads/sh
but if the file is there - do a:  file sh  - to see what kind of executable it is. 
cheers

---

