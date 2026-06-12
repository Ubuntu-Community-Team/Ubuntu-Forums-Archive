---
title: "Glipper not working (at all) in Gutsy"
date: 2007-12-06
forum: General Help
---

### Post by castawaybcn on 2007-12-06
Hi there,
I can't manage to get **Glipper** to work. I installed from **Synaptic** version **0.95.1-3** and everything seemed to work fine, found the launcher in Applications>Accessories but nothing seemed to happen. Went to System Monitor and the process was there though, I killed it and tried running it from the console just to get this message:
```
(process:9756): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed
```
Anyone has come up with a similar problem, and hopefully a solution?

I am guessing that this may have something to do with trayicons(?) in gnome Panel since [Zim]("http://pardus-larus.student.utwente.nl/%7Epardus/projects/zim/index.shtml") (v0.19) used to minimize there in Edgy and no longer does in Gutsy (clean install). The same seems to apply for Tomboy notes

Any help will be much appreciated
Thanks a lot

---

### Post by castawaybcn on 2007-12-07
nobody had this issue? Really?
Wow, I'm feeling special now :-?

---

### Post by Maybelline on 2007-12-10
Well, I just started seeing this behavior today.  I'm not sure what started it, but now my glipper won't run -- I get the "gnome_program_module_register: assertion `module_info' failed" message.

Strangely, this just started happening, and I have only been messing with evdev & my mouse driver.  Odd.

---

### Post by oldos2er on 2007-12-10
Maybe it's a glitch with the latest version. I've been running 0.95.1 for ages on Feisty and Gutsy and it works fine.

---

### Post by castawaybcn on 2007-12-10
Hi Maybelline,
I didn't find a solution so far, none to be expected coming from my own guesses since I am rather new to GNU/Linux, I'm afraid...
I will keep on searching and will post any findings I may come across in this thread though, I would appreciate if you were kind enough to do the same. In the meantime, some expert's advice would be much welcome :)

Tx for the answer anyways, I feel a little less bug-lonely ;)

---

### Post by castawaybcn on 2007-12-10
Hi oldos2er,
strangely enough it is version 0.95.1-3 (installed through Synaptic) that is giving me the trouble...
Any ideas where I could look for the problem?

Ta

---

### Post by oldos2er on 2007-12-10
Just noticed there's a Glipper v1.0 on gnomefiles.org .

---

