---
title: "XEmacs and SSHing help"
date: 2008-04-03
forum: General Help
---

### Post by rjim on 2008-04-03
Hi.

At my school computer lab, I am able to SSH to one of the Linux servers for programming.  I use ```
xemacs [filename] &
```.  From this, XEmacs opens up the file in it's own window for editing while allowing me to use the terminal window for compiling and whatnot.  However, on Ubuntu 7.10 (my laptop), when I attempt to do the same thing, the XEmacs window never shows.  Pressing ENTER suspends xemacs with the message ```
Suspended (tty output)
```.  Anyone know of a way to correct this?

Here's a sample output:
```
linux1[4]% xemacs proj1.c &
[1] 3859
linux1[5]% xemacs: /usr/lib/libdb.so.3: no version information available (required by xemacs)

[1]  + Suspended (tty output)        xemacs proj1.c
linux1[5]% 

```

However, using ```
xemacs [filename] &
``` works fine when opening a file that is located on my personal system.

Thanks.

---

### Post by gaussian on 2008-04-04
If I understand the problem correctly, I think you need to enable X-forwarding when you connect to the remote server from your laptop.

```

laptop$ ssh -X remoteserver.yourschool.edu
remoteserver$ xemacs project.c &

```

---

### Post by rjim on 2008-04-04
Awesome, it works fine now.  Thanks.

---

