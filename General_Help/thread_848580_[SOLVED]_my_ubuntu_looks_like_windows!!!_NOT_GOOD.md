---
title: "[SOLVED] my ubuntu looks like windows!!! NOT GOOD"
date: 2008-07-03
forum: General Help
---

### Post by Attila2452 on 2008-07-03
the colors for the themes on mu ubuntu are the same colors as Windows microsoft 95! this is really weird, because i have windows XP and ubuntu. last week i restarted my computer and wanted to go to ubuntu , and when i did it looked like Windows, like just the colors. like the menu, when i clicked it, it dropped down fine, but the OnMouseOver effect is the same as windows. i don't know what else to do, i have tried changing the theme and i even looked into the colors it is set to, its in Human. and the colors are orange, but my ubuntu shows blue. its so weird. i want ti changed.

 - Attila Hajzer -

---

### Post by ferrarix on 2008-07-03
Can you post some screenshots pls?

---

### Post by adamogardner on 2008-07-03
I changed that.  It's all under preferences>appearance if I'm not mistaking.

---

### Post by Attila2452 on 2008-07-03
[img]http://www.fileden.com/files/2008/3/30/1844325/help.png[/img]

---

### Post by unseend on 2008-07-03
I think you just have to change your theme. You are using Tango or what? For the ubuntu like theme go to System>PReferences>appearance and choose the Human theme. Hope I helped :D

---

### Post by Attila2452 on 2008-07-03
no it didn't ... so in the mean while, i was trying to fix my visual problem, i was trying to uninstall some things  and this is what popped up...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

I don't know what it is.... and on top of that, i don't know how to report anything.  a couple of times i have found a program called 'Bug Report Tool'  and then there is 'Report a problem', but the same thing shows up.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.


i neeed HELP!

---

### Post by pferpaddy on 2008-07-03
run sudo dpkg --configure -a in the terminal and itl fix itself
that dont work go to prefrences then files in synaptic and select clear cache the apply

---

### Post by bubba_169 on 2008-07-03
For you last problem, open a terminal and run

```
sudo dpkg --configure -a
```

For the first have you tried changing your theme to something else see if that works. Clearlooks maybe?

---

### Post by pferpaddy on 2008-07-03
and also youve uninstalled the theme engine you where using that why it looks like windows reinstall the theme engine if u want your theme back

---

### Post by Attila2452 on 2008-07-03
ok so i did that command:

sudo dpkg --configure -a


and after a minute or so, this is what showed up:

Errors were encountered while processing:
 libgksu2-0

now what do i do?

---

