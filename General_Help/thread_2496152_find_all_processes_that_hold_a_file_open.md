---
title: "find all processes that hold a file open"
date: 2024-03-15
forum: General Help
---

### Post by ValentynPrumers on 2024-03-15
I have opened a file called 'test' with kate. Wrote some text, wrote it to disk and kept kate open.  Then i tried to find which process is holding the file open.

```
#lsof ./test
```

Gives no results.

```
# fuser -vf ./test
```

```
# lsof | grep test
```

Also no results.

```
#lsof
```

Does give a lot of output

Also tried to open the file with vim (and hold it open). But still both commands dont give me any output. Also not when i use sudo. Also no results when i specify the
fullpath to the open file. System: Kubuntu 23.10.

---

### Post by dragonfly41 on 2024-03-15
I use an easy method. Install Stacer GUI, view running processes, search "kate".
But I'm sure you will get cli suggestions.

---

### Post by TheFu on 2024-03-16
```
sudo lsof | egrep -i test
```
is what I'd use.  Just tested it.  Looks like lsof has gotten really slow.  Took about 60 seconds before any useful output even started.  I'm guessing there's a timeout required now - probably another snap related issue.

Editors that are smart don't open files and hold them. They use a temporary file for modifications, then apply those when the "write" or "save" is requested.  I don't use kate, so I don't know how it works. I know the vim created a /tmp/.t.swp when I was editing /tmp/t.  /tmp/t didn't show up in the output, just the .swp file.

---

### Post by The Cog on 2024-03-16
fuser is nice and quick but only if you know a specific filename. If you can't umount a drive because it's "in use" then "sudo lsof | grep $mount_point" is the only way I know of. I' may be a little slow, (a couple of seconds on my current machine) but it's reliable.

---

### Post by ValentynPrumers on 2024-03-19
Thanks. For some reason # sudo lsof | grep test now does show me vi is using the file.

But ```
sudo  fuser -vf test 
``` Still does not produce any results. It does seem to work for commands. So if i execute

```
 tail -f /var/log/syslog 
```

and then on another terminal.

```
 fuser -v /usr/bin/tail
```

It does output the process that is using the tail command.

---

### Post by TheFu on 2024-03-19
> **ValentynPrumers said:**
> Thanks. For some reason # sudo lsof | grep test now does show me vi is using the file.
 

See/re-read post #3.

---

### Post by ValentynPrumers on 2024-03-20
Thanks. So processes that read files are not displayed with fuser.  What is the best way to find all processes that are using a certain file?

---

### Post by TheFu on 2024-03-20
> **ValentynPrumers said:**
> Thanks. So processes that read files are not displayed with fuser.  What is the best way to find all processes that are using a certain file?

lsof is the only way I know.  Just be less restrictive about the filename in the **egrep**.  It doesn't hurt to know how the program actually works.  Lots of programs will make a copy of the file to be edited, often using a random name, so that edit collisions don't happen.  Whoever writes the copy they'd been using last, wins.  This is how Unix has worked for 40+ yrs.  In a multi-user system, this is a design choice. The alternative is to have file locking and every process has to check for locks, potentially preventing any access to others.  I remember that Netware worked that way, so it was possible for someone to lock a file all day long, not allowing anyone else any access at all.

Concurrency issues are an important design consideration in multi-user systems.  There are times when both options fail, unfortunately.

---

### Post by Impavidus on 2024-03-22
> **TheFu said:**
> Lots of programs will make a copy of the file to be edited, often using a random name, so that edit collisions don't happen.Even if the program doesn't use a temporary file, it may not keep the file open. For a simple application, the typical use would be to open the file, read it to RAM, then close it. What's stored in RAM isn't a byte-for-byte copy of the file, but has a more practical structure. When saving the file, the application opens the file, writes the file from RAM (again, not an exact copy of what's in RAM), then closes the file. Unless you're talking about huge files, the file won't be open for more than a second each time.

---

