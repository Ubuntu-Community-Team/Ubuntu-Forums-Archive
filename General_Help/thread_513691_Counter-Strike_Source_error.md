---
title: "Counter-Strike Source error?"
date: 2007-07-30
forum: General Help
---

### Post by nu buntu on 2007-07-30
Ok, so here is my problem.  I installed CS and steam and all that and they work fine.  I got CS 1.6 up and working fully with 0 errors.  But CSS is a different story.  I can launch CSS ok, I can make a server/join one ok.  But the second before I get into the game, it freezes/crashes so I either have to reboot/crtl+alt+backspace.  I think I have the OSS setting in winecfg set properly, but I am not sure.  If anyone knows how to fix this, then please help me.

A screen of my winecfg:

[IMG]http://img170.imageshack.us/img170/7694/winecfguh5.png[/IMG]

---

### Post by nu buntu on 2007-07-30
bump

---

### Post by nu buntu on 2007-07-31
bump

---

### Post by nu buntu on 2007-07-31
Doesn't anyone know the answer?

---

### Post by Swarms on 2007-07-31
Try typing this into a terminal:
```
cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240
```

Btw. if it works, someone please tell me how to make a launcher with that command, every try I did failed.

---

### Post by nu buntu on 2007-08-01
Well, its not launching that I have a problem, but I will try with this.

---

### Post by nu buntu on 2007-08-01
Well, that only made it worse, now it won't even load.  It launches, I see the loading screen, then it closes off.  Sorry, but that command did nothing for me.

---

### Post by nu buntu on 2007-08-01
I changed the question and added screens now so it is more easily understandable.

---

### Post by nu buntu on 2007-08-01
bump

---

### Post by nu buntu on 2007-08-01
bump

---

### Post by nu buntu on 2007-08-01
bump

---

### Post by nu buntu on 2007-08-02
bump

---

### Post by theonlyalterego on 2007-08-02
adding 'bumps' will not help solve your problem, you're more likely to get a reply if it looks like less people have helped you.

That said, I too am having CSS issues, but they appear to be different from your. I can start steam, but when I try and launch CSS I get a 'registry already in use error'

---

