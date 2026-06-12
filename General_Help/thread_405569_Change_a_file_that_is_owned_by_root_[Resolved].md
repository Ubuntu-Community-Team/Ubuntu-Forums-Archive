---
title: "Change a file that is owned by root [Resolved]"
date: 2007-04-09
forum: General Help
---

### Post by kodiak41226 on 2007-04-09
Basically the other day I created a text file while in sudo mode in the terminal. Now I would like to copy that text file to my Windows 2003 Server through Samba, and I cannot get the file to copy, although everything else in Samba appears to work great. The text file has the little lock icon above it, and when I try to change the permissions, I cannot because root is the owner. I've been reading about file permissions for a couple hours now and trying things, but I cannot change the owner or permissions. I have to think that there is a simple way to fix this. Any ideas?

---

### Post by WiseElben on 2007-04-09
You should try:

```

$ sudo chown *your_username* file.txt

```

This will set you as the owner of the file.

You can also try starting nautilus in sudo by typing:

```

$ sudo nautilus

```

---

### Post by aysiu on 2007-04-09
Never use *sudo* with a graphical application. It should be ```
gksudo nautilus
``` **not** ```
sudo nautilus
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

And Nautilus will work only if you're using Ubuntu. If you're using Kubuntu or Xubuntu, you'll need ```
kdesu konqueror
``` or ```
gksudo thunar
``` respectively. More details here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by kodiak41226 on 2007-04-09
That worked for me, Thanks. 

The strange thing is I tried that same sort of thing, when I was searching for a solution and it didn't work for one reason or another, I dunno. 

Thanks Again.

---

