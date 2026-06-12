---
title: "Help, I can't move fonts! D:"
date: 2007-02-23
forum: General Help
---

### Post by t.z0n3 on 2007-02-23
I just can't do it. Here's what I try to do, and I'm root right now, so it SHOULD work. 

root@matthew:/home/matthew/Desktop/Pokemon Card Project# mv Humanist521BT.zip_FILES/ ~/home/usr/share/fonts/truetype

That's where it should go, I think. I even checked. The folder '/' is root, right? That's where you start from, right? I just don't get it. :confused:

---

### Post by llamakc on 2007-02-23
The tilde character "~" translates in the shell to being the current users's home directory.

So what you typed as the destination:

~/home/usr/share/fonts/truetype

would mean you're trying to write to:

/root/home/usr/share/fonts/truetype

when you probably want /usr/share/fonts/truetype instead.

---

### Post by taurus on 2007-02-23
Shouldn't the fonts be in the font directory like /usr/share/fonts?

```
mv Humanist521BT.zip_FILES/*  /usr/share/fonts/truetype/
```

---

### Post by t.z0n3 on 2007-02-23
It worked, thank you very much. I didn't know that the dumb tilde meant home... hehe... ^^;

---

