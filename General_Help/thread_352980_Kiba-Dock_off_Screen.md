---
title: "Kiba-Dock off Screen"
date: 2007-02-04
forum: General Help
---

### Post by fokuslee on 2007-02-04
Help, i just installed kiba-dock from an old deb i found on beryl forums.  
after i start it it sits outside the view of my screen, i only see it hanging at the bottom of the cube when i rotate cube  (i have beryl) 
how do i fix this?
does it have anything to do with 
XAANoOffscreen pixmaps?

ps if anyone recenlty made 64bit version please upload thx in advance

---

### Post by loell on 2007-02-04
that's a known bug, just restart it.

---

### Post by c0nv1ct on 2007-02-28
I'm having the same problem, i've been searching the forums and can't seem to find a solution.

Every time I start kiba-dock, its below my screen.  As the OP said, I can see it when rotating the cube but I can't access the dock what-so-ever.  Restarting it does nothing.

---

### Post by ryckmonster on 2007-03-01
try draggin an icon to it from the applications drop down tab

---

### Post by lukew on 2007-03-01
I have the same problem if I started kiba-dock from Alt-F2 or from an icon. It falls from the roof and keeps on going past the bottom. Sometimes it settles top left but has all icons on top of each other.  It was not doing this untill the other day. I tried reinstalling it from debs on the forum and also recompiling from cvs; still the same problem.

It is ok if i run it from the terminal.

The application does seema  bit flaky FULLSTOP. You change mode and it crashes. Often the icons wont sit in a line properly or they start sitting in the wrong place.

Luke

---

### Post by ryckmonster on 2007-03-02
> **ryckmonster said:**
> try draggin an icon to it from the applications drop down tab

Do what i say

---

### Post by MrFahrenheit on 2007-03-12
> **ryckmonster said:**
> Do what i say
How do you drag an icon to it if it's offscreen?  I'm having the same issue.

---

### Post by lukew on 2007-03-13
> **MrFahrenheit said:**
> How do you drag an icon to it if it's offscreen?  I'm having the same issue.

Hay I noticed that on mine it worked ok if I ran it from a terminal but not from the startup application or from Alt-F2. 

Copy the following into a file called start_kiba.sh



```

#!/bin/sh

# File:   start_kiba.sh
sleep 10 && kiba-dock;  

```

Make it executable

```
 chmod +x start_kiba.sh
```

Add that into your startup instead of 

```
kiba-dock
```

---

