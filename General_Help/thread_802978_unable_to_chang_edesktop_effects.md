---
title: "unable to chang edesktop effects"
date: 2008-05-21
forum: General Help
---

### Post by zeroprezens on 2008-05-21
hi, first time posting, but ive been an ubuntu user for about 10 months, anyway; im on mint Daryna (based off of gusty) and when i go to change what desktop effects are used, i can check all the boxes, but nothing happens. all i really want is either burn or magic lamp, but it keeps the original compiz minimize effect. as a matter of fact, i cant actually change any effects. it says theyre enabled but still nothing. ive tried disabling all of the effects except magic lamp or burn or any of them and still nothing ><

ive also tried restarting compiz with the command in terminal and ever restarting' but still nothing. 


any help is appreciated; ive googled for about a week and cant find anything helpful at all, i just want a minimize effect is tat too much to ask? :confused::(

---

### Post by zeroprezens on 2008-05-21
urgent help!

i just ran compiz in the terminal and it applied some of the effectn, but my window management bar is gone, luckily i can use keyboard shortcuts, but this is still definantly goingg to be an issue

i ran replace -- metacity but that didnt do anything


help!:mad:

---

### Post by atomkind on 2008-05-22
I'm not sure what you mean by window management bar... but had a problem in openSuse where compiz disappeared my tiblebars (this is where the 'minimize|restore|close' buttons live). This is a long shot but if this is your case try running ```
gtk-window-decorator --replace
```

---

### Post by Forlong on 2008-05-22
> **zeroprezens said:**
> i ran replace -- metacity but that didnt do anything
The proper command is
```
metacity --replace
```

---

