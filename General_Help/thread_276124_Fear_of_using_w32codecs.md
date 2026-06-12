---
title: "Fear of using w32codecs"
date: 2006-10-12
forum: General Help
---

### Post by ianmacgregor on 2006-10-12
I've been using Ubuntu since Warty and I love this awesome distro. I used Feora before Ubuntu and debian before that. I haven't used Windows in years because Linux just seems to be so much better.

I have a friend who uses Windows software to create videos in wmv format. Since I know how easy it is for someone to write a virus/rootkit and rename it to newvideo.wmv, I have a few questions.

I know that a virus can re-write .dll files or install other files/apps.

So..
1. How safe is it to use w32codecs to view wmv files in Ubuntu?
2. How safe is it to view wmv files altogether in Ubuntu?
3. The w32codecs package installs .dll files. Can a virus re-write those .dll files or install something that "listens" for the user to type the root password via sudo/gksudo?
4, What are some things that I **shouldn't** be doing in Ubuntu with regard to Windows stuff?

Thank you in advance :)

---

### Post by PriceChild on 2006-10-12
> **ianmacgregor said:**
> 1. How safe is it to use w32codecs to view wmv files in Ubuntu?As a user, perfectly safe.
As a staff member, i advise you to stick to official repositories for stability.
> 2. How safe is it to view wmv files altogether in Ubuntu?If you're that scared, i think you can install "vlc" player to play them with. Bit uglier... but works, and may play more formats than normal codecs allow.
> 3. The w32codecs package installs .dll files. Can a virus re-write those .dll files or install something that "listens" for the user to type the root password via sudo/gksudo?Hasn't happenned yet... doubt it will! You would have to give root privelages to it in order to even listen as far as i understand.
> 4, What are some things that I **shouldn't** be doing in Ubuntu with regard to Windows stuff?Nothing really that you shouldn't be doing... It's not too easy to mess up linux unless you give sudo permissions to things that don't need it... and even then its hard.

---

### Post by whizbaby on 2006-10-12
> **ianmacgregor said:**
> 
3. The w32codecs package installs .dll files. Can a virus re-write those .dll files or install something that "listens" for the user to type the root password via sudo/gksudo?

A windoze virus will only work if you manage to make it work in wine. Why should installing a .dll give a virus root privileges (it would need for installing a keylogger or similar)?

---

### Post by ianmacgregor on 2006-10-12
> **PriceChild said:**
> As a user, perfectly safe.
As a staff member, i advise you to stick to official repositories for stability.
If you're that scared, i think you can install "vlc" player to play them with. Bit uglier... but works, and may play more formats than normal codecs allow.
Hasn't happenned yet... doubt it will! You would have to give root privelages to it in order to even listen as far as i understand.
Nothing really that you shouldn't be doing... It's not too easy to mess up linux unless you give sudo permissions to things that don't need it... and even then its hard.

Thank you for the reply.. and for the good advice you gave in reply to question 1 :)

---

### Post by ianmacgregor on 2006-10-12
> **whizbaby said:**
> A windoze virus will only work if you manage to make it work in wine. Why should installing a .dll give a virus root privileges (it would need for installing a keylogger or similar)?

Hmm.. I don't use wine. I'm just cautious when it comes to installing stuff is all. Thanks for the help :)

---

### Post by whizbaby on 2006-10-12
Being careful is not bad when in front of a computer. Currently you are a lot safer on linux, and I don't believe this will discontinue.

---

