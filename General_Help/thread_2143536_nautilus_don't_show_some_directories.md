---
title: "nautilus don't show some directories"
date: 2013-05-09
forum: General Help
---

### Post by chinmay3 on 2013-05-09
Hello everybody.
I have Ubuntu lucid lynx installed on my desktop. Recently i have created some directories in my home folder. But when i open my home folder they are not there. when opened through gnome-do they get opened in nautilus. What i want to say is nautilus doesn't shows directories which are actually present in it. ( these directories are not hidden too , i checked by pressing ctr+h). Does anyone know why it is so?

Thanks in advance.:confused:

---

### Post by PowerBarry43 on 2013-05-09
Hi

Sounds like it could be a bug, I take it you're running up to date nautilus. You could also try a different file manager such as dolphin and see if the problem persists. Can you post the output of:

```
ls -al ~/
```

Barry

---

### Post by VanillaMozilla on 2013-05-09
Nautilus sometimes takes some time to find newly created files.  Perhaps related to [this bug.](https://bugzilla.gnome.org/show_bug.cgi?id=606993)

---

### Post by chinmay3 on 2013-05-11
sorry to say but i havn't updated for last 3 months. ( i will do as soon as possible).
& output is as in attachment.

---

### Post by PowerBarry43 on 2013-05-13
Hi

Permissions on the file look normal. My guess would be that your problem is nautilus. An update may fix it, otherwise you could try making a new directory and copying the contents of the old one into the new one by running from a terminal:

```
cd
mv "HP Recovery disks" "HP Recovery disks.old"
mkdir "HP Recovery disks"
cp "HP Recovery disks.old/*" "HP Recovery disks/"

```

Hope this helps!

Barry

---

### Post by chinmay3 on 2013-05-13
Thanks for your kind help. I will try updating system.

---

### Post by billcauley on 2013-05-13
I came across this yesterday:
[http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html](http://www.webupd8.org/2013/04/get-nautilus-34-features-back-in-ubuntu.html)

---

