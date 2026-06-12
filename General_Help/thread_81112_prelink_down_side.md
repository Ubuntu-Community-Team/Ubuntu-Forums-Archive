---
title: "prelink down side"
date: 2005-10-23
forum: General Help
---

### Post by kroiz on 2005-10-23
hi, what is the trade off for the speed gained by prelink, if any?

---

### Post by xombie on 2005-10-23
Applications launch faster with prelinking. Without prelink applications link with dependencies at launch.

---

### Post by kroiz on 2005-10-23
[QUOTE=xombie]Applications launch faster with prelinking. Without prelink applications link with dependencies at launch.[/QUOTE]
So... all my application will run faster all the time?

---

### Post by xombie on 2005-10-23
No, they do not run faster, they startup faster.

---

### Post by kroiz on 2005-10-23
[QUOTE=xombie]No, they do not run faster, they startup faster.[/QUOTE]
ok, that is great, but does it come on expense of something else?
becase usually you dont get something for nothing. so what is the catch?

---

### Post by Kyral on 2005-10-23
If you dont enable prelink after Apt-Get operations, you could get messed up with libraries being updated and Prelink still pointing to the old ones

---

### Post by kroiz on 2005-10-23
[QUOTE=Kyral]If you dont enable prelink after Apt-Get operations, you could get messed up with libraries being updated and Prelink still pointing to the old ones[/QUOTE]
now you're scaring me. 
can you just put in terms of pros and cons.

---

### Post by Kyral on 2005-10-23
Thats the only con I can think of. But just folow the guide on the Forums (In one of the Customization Forums) and you'll be fine. I've been running Prelink for 5 months now and no probs (at least caused by Prelink)

---

### Post by VR6Pete on 2005-10-23
I've been using prelink for some time now, no problems here either.

Just follow the guide that's available on this forum.

---

### Post by kroiz on 2005-10-23
ok Im satisfied. it sure is a keeper.
thanks guys.

---

### Post by Xian on 2005-10-23
I've only noticed an improvement on KDE apps.
I don't even use prelink with a strictly Gnome desktop.

---

### Post by monkey89 on 2005-10-23
The con is that it takes up more hard drive space.  If you have plenty of it, it's fine.

---

### Post by AndersAA on 2005-10-23
[QUOTE=Kyral]If you dont enable prelink after Apt-Get operations, you could get messed up with libraries being updated and Prelink still pointing to the old ones[/QUOTE]

if I remember correctly this isn't an issue

[QUOTE=Xian]I've only noticed an improvement on KDE apps.
I don't even use prelink with a strictly Gnome desktop.[/QUOTE]

prelink helps on C++ libraries, and not on C (if I remember correctly), most of kde is c++, so it helps a lot there, while gnome is mostly pure C, so it doesn't help there.

---

