---
title: "what's the benefit of .fuse_hiddenxxxxxx files?"
date: 2013-06-02
forum: General Help
---

### Post by mbnoimi on 2013-06-02
I'm wondering what's the benefit of .fuse_hiddenxxxxxx files?

I've ton of them and I periodically remove them manually which really painful procedure!

---

### Post by mbnoimi on 2013-06-05
bump

---

### Post by mbnoimi on 2013-06-08
I didn't face same issue when I used Nemo under Cinnamon desktop.

---

### Post by tgalati4 on 2013-06-08
Fuse is file system in user space:

```
man fuse
```

There is a switch in /etc/fuse.conf that allows up to 1,000 fuse mounts per user.  Perhaps lower that number.  Since fuse is a framework, several other programs use it.  If those programs quit unexpectedly or if there is a bug, you might have left over stuff in your home directory.  What program is creating these fuse mounts?

Other tools used with fuse:

```
apropos fuse
```

What is the benefit of these hidden fuse files?  Who knows?  What program is creating them?  What are you doing to create fuse mounts?  If you delete them, they will probably be recreated.  What is in the files?  Are they binary files or text files?

---

### Post by mbnoimi on 2013-06-09
> What is the benefit of these hidden fuse files? Who knows? What program is creating them? What are you doing to create fuse mounts? If you delete them, they will probably be recreated. What is in the files? Are they binary files or text files? 
Actually I'm using truecrypt so it may is the reason of these files but truecrypt doesn't occur any problem! How can I be sure 100%? is there any log or something similar?

---

### Post by tgalati4 on 2013-06-09
Typically mounts require root privilege and they are documented in /var/log/auth.log, but fuse mounts are done in user space, so they may be recorded elsewhere.  So look at all the log files in /var/log for clues.

---

### Post by mbnoimi on 2013-06-09
> **tgalati4 said:**
> Typically mounts require root privilege and they are documented in /var/log/auth.log, but fuse mounts are done in user space, so they may be recorded elsewhere.  So look at all the log files in /var/log for clues.

I opened KSystemLog I couldn't know from where I've to start, which term I've to look for? I just need the key words which point to the problem trace.

---

### Post by mbnoimi on 2013-06-09
By the way, I noticed that the number of these files increases after copy or cut process.

---

### Post by tgalati4 on 2013-06-09
Search for fuse or FUSE in the log files.

```
grep fuse /var/log/*
sudo grep -R fuse /var/log/*
```

---

