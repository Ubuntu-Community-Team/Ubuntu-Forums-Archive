---
title: "using mv and grep to move a list of files"
date: 2008-05-17
forum: General Help
---

### Post by bbbaldie on 2008-05-17
I have about 15,000 jpgs in nested directories. I have managed to use the locate command (thanks for that, Red Hat!) to create a text file that shows the path of every single jpg. Now, what I want to do is pipe the contents of that file to a mv command to put all of those files in one folder.

I've done lots of searches for mv and grep, but have yet to find this particular situation addressed.

It's probably drop-dead simple, but I'm stuck. To recap:

mv (list of files in text file) ../images.

Thanks, gang.

---

### Post by Monicker on 2008-05-17
You can run this from a terminal:

```
cat list.txt | while read line; do mv "$line" /images; done
```

---

### Post by bbbaldie on 2008-05-17
> **Monicker said:**
> You can run this from a terminal:

```
cat list.txt | while read line; do mv "$line" /images; done
```

Perfect! Just the kind of instant info I've come to expect from Ubuntu forums!

Thanks a bunch. My processors are currently pegged moving a whole slew of files :-)

:guitar:

---

### Post by here2serve on 2009-12-28
Thanks. You saved the day. I had a mail folder with 87 Mill to sort through. At little grep and your post went a long way.

---

