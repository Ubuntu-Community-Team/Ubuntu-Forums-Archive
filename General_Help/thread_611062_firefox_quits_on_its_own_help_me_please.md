---
title: "firefox quits on its own help me please"
date: 2007-11-12
forum: General Help
---

### Post by Faceplant15000 on 2007-11-12
Today for some reason firefox decides to close when ever i leave the hopepage. I reinstalled it and it didnt work. Im new to linux and any help would be greatly appreshieated.

---

### Post by Thyme on 2007-11-12
Hi Faceplant15000,

Can you please provide the output of the following command:

```

ldd /usr/bin/firefox

```

This checks whether you have all the necessary libraries for your extensions etc .. )

---

### Post by Faceplant15000 on 2007-11-12
when i tried it it said "not a dynamic executable" I have no clue what that means.  I also tried other web browsers and they all do the same thing. As soon as i leave the home page they quit.

---

### Post by Faceplant15000 on 2007-11-13
is there anyone who can help me. Should I reinstall ubuntu? Can a live CD help. Please This is really starting to annoy me.

---

### Post by AlexThomson_NZ on 2007-11-13
Run it from a console, and see if that comes up with any warnings/errors

---

### Post by Sef on 2007-11-14
> Run it from a console, and see if that comes up with any warnings/errors

Alt + F2 > then type in Firefox.  Note: you have to type it in exactly as it is spelled.  If you get any errors, then copy and post them here.

---

### Post by geirha on 2007-11-14
it's probably something in the configuration it doesn't like for some reason. If you move away .mozilla in your homedirectory, it should come up as though it was a fresh install. All your bookmarks and other configuration are in the .mozilla dir though ... 
```
mv ~/.mozilla ~/.mozilla.backup
```
It really shouldn't close on you like that though, so it's probably a bug in firefox, at least if it runs fine after you move away your .mozilla dir.

---

### Post by RogueRunner on 2007-11-14
> **geirha said:**
> it's probably something in the configuration it doesn't like for some reason. If you move away .mozilla in your homedirectory, it should come up as though it was a fresh install. All your bookmarks and other configuration are in the .mozilla dir though ... 
```
mv ~/.mozilla ~/.mozilla.backup
```
It really shouldn't close on you like that though, so it's probably a bug in firefox, at least if it runs fine after you move away your .mozilla dir.

Tried that already to no avail! This affect ALL my mozilla apps though, thunderbird crashes if I try to delete something! I a pretty sure it started happening after the previous updates I applied! Is there a way to rollback?!??

---

### Post by SpiritIsReality on 2007-11-14
howdy
I don't know why, but here's some crashes
[http://www.google.ca/search?as_q=&hl=en&num=10&btnG=Google+Search&as_epq=firefox+crashes&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m2&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=&hl=en&num=10&btnG=Google+Search&as_epq=firefox+crashes&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m2&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
trails

---

### Post by geirha on 2007-11-14
yes @RougeRunner ```
mv ~/.mozilla ~/.mozilla.foo
mv ~/.mozilla.backup ~/.mozilla
```

---

### Post by Faceplant15000 on 2007-11-16
ok I ran it from the termanal and it did the samething and didnt give me an error log. What now??

---

### Post by Faceplant15000 on 2007-11-16
ok never mind I did something that fixed it. I rolled it back and now it works fine. Thank you for all of the Help Id be stuck with out these forums.

---

### Post by SpiritIsReality on 2007-11-17
> **Faceplant15000 said:**
> ok never mind I did something that fixed it. I rolled it back and now it works fine. Thank you for all of the Help Id be stuck with out these forums.

That's the Spirit pard.I'd be stuck in first gear on the starting lineeeeee.

---

