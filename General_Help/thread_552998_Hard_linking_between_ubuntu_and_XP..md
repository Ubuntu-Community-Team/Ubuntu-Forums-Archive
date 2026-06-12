---
title: "Hard linking between ubuntu and XP."
date: 2007-09-17
forum: General Help
---

### Post by vampire666eng on 2007-09-17
I was thinking if it was possible to share the programs settings of XP with ubuntu without having to copy every time the settings from a drive (with the other OS) to another.

Basically I would like to share firefox , thunderbird and utorrent settings (but also other programs) between these two OS. So all the setting of FF and the stats and torrents of utorrent are always right and updated even if I change the OS session.

I already successfully did something similar between Vista and XP (so if you want to do something similar just do as I did). 
I just used the &#8220;Hard Link Shell Extension&#8221; ([http://schinagl.priv.at/nt/hardlinkshellext/hardlinkshellext.html](http://schinagl.priv.at/nt/hardlinkshellext/hardlinkshellext.html) I linked (hard linked) the setting directory of the programs (Firefox and utorrent) between the two different partitions (managed by the two OS), and voilà...problem solved.

Is there something similar that I can use with ubuntu -- XP?

(P.S. I know that utorrent isn't supported for linux (oh well...I could just use WINE ;))...it was just an example)

---

### Post by vampire666eng on 2007-09-17
The main quastion is...does hardlinks exist in ubuntu?
If yes....how to enable them?

---

### Post by wirelessmonkey on 2007-09-17
Yes, they're called simlinks, they are invoked by "ln -s"
I highly suggest you read: man ln

---

### Post by vampire666eng on 2007-09-17
Thank you.

I'll immediately check it out. :)

---

### Post by vampire666eng on 2007-09-17
Nice. Thanks.
Is there something with a GUI that can perform easily these steps for who (like me) isn't really comfortable (yet) with terminal text (yes...Windows spoiled me dammit!).

Tx.

---

### Post by vampire666eng on 2007-09-17
So if there isn't a graphical interface please help me out with the commands I should put:
If for example I want to simlinks a directory on drive c:\ (C:\Mozilla\Thunderbird) in a ubuntu partition directory....what should I do?

Thanks.

---

### Post by bodhi.zazen on 2007-09-17
Open nautilus

Navigate to the directory/document you want to link to 

Right click on the directory/document, select "make link"

Now drag the link where you want it.

This will be a soft link, but it should not matter, (I hope).

---

### Post by vampire666eng on 2007-09-17
Wow, a forum staff reply. Couldn't be more lucky!;) 
I'll check that immediatly.

Thanks a lot!

---

### Post by vampire666eng on 2007-09-18
Thank you. Just wanted to tell you that it works perfectly.

Cheers.

---

### Post by bodhi.zazen on 2007-09-18
You are most welcome. 

Welcome to Ubuntu :twisted:

---

