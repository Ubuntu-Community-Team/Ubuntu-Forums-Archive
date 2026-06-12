---
title: "Way to keep splash-screen until gnome fully loads?"
date: 2008-02-24
forum: General Help
---

### Post by novellterminator on 2008-02-24
Hello there Ubuntarians! My question is simple: Is there any way to keep the Ubuntu splash-screen up (the screen with the progress bar) while gnome loads?

Gnome on my computer takes a good 10+ seconds to start (I don't like sitting there watching a black screen :)), and I'd like to know if I could just see the progression of gnome loading via the progress bar. (I've already set up the computer to automatically log me in.)

Any thoughts?

Derek

---

### Post by pointone on 2008-02-24
You could try editing /etc/init.d/usplash, and changing line 60:

```
# ask usplash to go away
usplash_write QUIT
```

```
# ask usplash to go away... soon
usplash_write "TIMEOUT 15"
```

Not sure if this will work or not, but it shouldn't hurt to give it a shot. 

You could also try changing the symlink in /etc/rc2.d from S98usplash to S99usplash, so it's the absolute last thing stopped. Seeing how it's already S98, though, I doubt this would do much.

---

### Post by blankz on 2008-02-28
it didnt work.. but my graphical view just stop working. when I did a reboot I just get a text-prompt where I can log in :\

---

