---
title: "In which directory are the applications?"
date: 2005-10-26
forum: General Help
---

### Post by autonomy on 2005-10-26
I just installed RealPlayer 10 to the Desktop. In which directory are the applications, and how do I move the RealPlayer folder there?

---

### Post by Xian on 2005-10-26
You could move it to a path like /usr/bin

Or just remove that file/folder and install realplayer by:

1. Include the [Multiverse Repositories](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse) in your source list.

2. Update your source list.

```
$ sudo apt-get update
```

3. Install realplayer.

```
 $ sudo apt-get install realplayer
```


```
$ sudo apt-cache policy realplayer
realplayer:
  Installed: (none)
  Candidate: 8.0.11
  Version table:
     8.0.11 0
        500 http://us.archive.ubuntu.com breezy/multiverse Packages
        100 /var/lib/dpkg/status
```

---

### Post by Xian on 2005-10-26
[QUOTE=autonomy]...how do I move the RealPlayer folder there?[/QUOTE]

Sorry, didn't read all of your post.

Move it like this:

```
$ cd /home/username/Desktop
$ sudo mv RealPlayer /usr/bin
```

---

### Post by autonomy on 2005-10-27
thanks :)

---

