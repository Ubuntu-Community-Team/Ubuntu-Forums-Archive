---
title: "Where are Sunbird .ics files stores?"
date: 2006-12-23
forum: General Help
---

### Post by crthomas on 2006-12-23
I am trying to use FinchSync to sync my smartphone with my calendar in Sunbird, but I can't find the files.

---

### Post by eylisian on 2006-12-23
locate is a decent way to look. first update the local db with;
```
sudo updatedb
```
then you can churn through the filesystem with;
```
sudo locate *.ics
```

hope it helps.

---

### Post by crthomas on 2006-12-23
The only files I found were in evolution.  Is it possible that Sunbird is using the same files?

---

