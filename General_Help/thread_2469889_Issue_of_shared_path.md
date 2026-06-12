---
title: "Issue of shared path"
date: 2021-12-12
forum: General Help
---

### Post by peter-1984 on 2021-12-12
Hi,
If there is one shared path like


\\my.own.ip.addr\sh_path


how to access it within Ubuntu?

---

### Post by TheFu on 2021-12-13
don't use \ characters.  Use  //my.own.ip.addr/sh_path inside any file manager. That should work, if the required client libraries are installed.  There are 2 methods to mount storage ... the GUI will be significantly slower than doing it at the OS level in the /etc/fstab file. The fstab method  would use a cifs mount line and should be at least 30% faster - sometimes 300% faster. It just depends on the remote system and what that machine is running for the OS.

How to do these things is something that Morbius1 has posted about many, many, times in these forums.  There are lots of specifics based on the version of the protocol being used, the exact client OS, the exact server OS.

---

### Post by peter-1984 on 2021-12-13
Hi,
How to get into specific shared path below?

<snip>

---

### Post by QIII on 2021-12-13
@peter-1984

Rather than posting a random URL which could be anything -- and which a cautious user like me would not dare opening -- why don't you simply post the shared path?

---

### Post by peter-1984 on 2021-12-13
I also use scp to do the copy from remote shared path. How to resolve it below regarding port 22?

---

### Post by Morbius1 on 2021-12-14
> **peter-1984 said:**
> Hi,
If there is one shared path like


\\my.own.ip.addr\sh_path


how to access it within Ubuntu?
I am confused by your post.

\\my.own.ip.addr\sh_path is the way a Windows machine denotes an SMB shared folder. In Linux you need to tell the file manager that SMB is the protocol being used:

So in the location bar in Nautilus ( Files ) it would look like this:
```
smb://my.own.ip.addr/sh_path
```

---

