---
title: "watching for changes anywhere in a file system"
date: 2020-02-16
forum: General Help
---

### Post by Skaperen on 2020-02-16
is it possible to have a watch scope over a whole file system, instead of filling up the kernel with millions of individual watches?

---

### Post by HermanAB on 2020-02-17
Maybe read up on tripwire.

---

### Post by Skaperen on 2020-02-18
tripwire is entirely unsuitable.  it keeps a checksum for each file and has to scan everything to look for changes.  for millions of files, the performance would be impractical.

---

### Post by dragonfly41 on 2020-02-18
Does inotify fit the bill ?

The  inotify API provides a mechanism for monitoring filesystem events.
       Inotify can be used to monitor individual files, or to monitor directo&#8208;
       ries.   When  a  directory is monitored, inotify will return events for
       the directory itself, and for files inside the directory.

---

### Post by Skaperen on 2020-02-19
inotify was the first (and only) tool i have looked at.  it wants me to identify every individual file or directory to be checked.  i have not seen any means to get a notification for a file system (a mount point or mounted device) for an event anywhere within that file system.  i am thinking that i will need to do this by implementing my own file system driver an just report

---

### Post by Skaperen on 2020-02-20
i think what i need is to modify the source of something simpler like overlayfs.  that way it will get every operation and can stream those to another process that records or reacts to the events of interest.  my current interest is anything that is renamed anywhere in the whole filesystem of about 4.8 million files.  the idea is to replicate the renames in the backups to reduce the backup traffic due to renames.

---

