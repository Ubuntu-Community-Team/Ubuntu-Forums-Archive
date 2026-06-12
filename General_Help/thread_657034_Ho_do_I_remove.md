---
title: "Ho do I remove?"
date: 2008-01-03
forum: General Help
---

### Post by Comhra on 2008-01-03
I have a file on my desk.  It's a faulty script that I was trying to use to install Songbird.  It's got a padlock in one corner and an X in the other.  I want to get rid of it but dragging it to trash doesn't work.  How do I dispose of it?

---

### Post by kpkeerthi on 2008-01-03
Open terminal and type 
[B]
1. cd Desktop
2. sudo rm the-file-on-my-desktop[/B]

---

### Post by Comhra on 2008-01-03
Included a screenshot of it.

---

### Post by Comhra on 2008-01-03
Can't do it.  Terminal say: no such file etc.  Is there another way?

Think I changed the extention.  Tried:  sudo rm installsongbird.sh. No luck

---

### Post by ukripper on 2008-01-03
> **Comhra said:**
> Can't do it.  Terminal say: no such file etc.  Is there another way?

Think I changed the extention.  Tried:  sudo rm installsongbird.sh. No luck

Find the file name using follwoing command in directory where you saved it and then remove:

```
ls - l
``` or simply do ```
ls
```

Note: l is small 'ell' not 1

---

### Post by Comhra on 2008-01-03
saved it to the desktop.  terminal says no such file or directopy

---

### Post by ukripper on 2008-01-03
in terminal type :

```
cd Desktop
```

```
ls
```

---

### Post by Comhra on 2008-01-03
seems to be in  /home/user/.Trash/installsongbird.

---

### Post by kpkeerthi on 2008-01-03
A file in your trash appears on the desktop. Hmm.. That's strange.

---

### Post by Comhra on 2008-01-03
Got it.  A log out/ log in was what the terminal needed to clean it out.  Thanks guys

---

### Post by ukripper on 2008-01-03
Great.

---

