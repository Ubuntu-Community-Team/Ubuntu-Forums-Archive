---
title: "Storing Files in the &quot;File System&quot; Section"
date: 2007-12-22
forum: General Help
---

### Post by neilrizo on 2007-12-22
Would it be possible to temporarily store files in "File System" Section of Ubuntu?

---

### Post by scxtt on 2007-12-22
are you talking about this?

---

### Post by neilrizo on 2007-12-22
> **scxtt said:**
> are you talking about this?

Yes sir! That's exactly what i was referring to.

I allotted a bit too much space for that section (around 5GB) and I was put it to good use - instead of it just lying around unused.

Can I use it, you think?

---

### Post by scxtt on 2007-12-22
do you have separate partitions for /home, /var, /tmp, etc.?

you'd have to be root to store files there, but it's def. possible.

---

### Post by weblordpepe on 2007-12-22
Yeah the folder system in linux/unix is much different to that of Windows. Basically all the files are there to be shared amongst applications, instead of hiding in their own Program Files directory.
You'll want to make a folder (while being root) and then change the permissions of that folder so your normal user can access it.

---

### Post by neilrizo on 2007-12-27
Hey guys! I was able to store my files on a temporary folder I made on the "File Section". But after deleting that folder my free space remains the same - as if that temporary folder was still there.

Why is this so? What should I do to regain that space?

---

### Post by taurus on 2007-12-27
Make sure you empty your trash bin too.

---

### Post by neilrizo on 2007-12-27
> **taurus said:**
> Make sure you empty your trash bin too.

Yup! I made sure that it was empty too.

Any other suggestion?

---

### Post by taurus on 2007-12-27
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
du -h ~/.Trash
```

---

### Post by neilrizo on 2007-12-27
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
du -h ~/.Trash
```


Perfect! The files/folders that I deleted were all there. Now I have my space back.

Thank you very much!

---

