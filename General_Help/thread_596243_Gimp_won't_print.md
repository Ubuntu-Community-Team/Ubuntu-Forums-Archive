---
title: "Gimp won't print"
date: 2007-10-29
forum: General Help
---

### Post by beengone on 2007-10-29
I set up a Dapper Xubuntu machine for my Grandpa and got a call the other day which I troubleshot over the phone w/vnc.  I can print from gview and firefox fine, but nothing prints from Gimp.  I'm trying to print photos, so Gimp makes the most sense.  Often, when I try to print from Gimp, it hangs the print queue completely.  I've heard something about needing special drivers for GIMP and looked a little at GIMPprint and GutenPrint, but I must be misunderstanding; I should have to install extra drivers when the printer is installed and working, right?  

In any case, could someone please help me figure out how to print to my HP printer from Gimp on Dapper?

Thanks

---

### Post by Spelley on 2007-11-04
I had problems with the new 2.4 version in my upgrade to Gutsy. The Gutenprint dialog crashed whenever I tried to print. I deleted the hidden .gimp-2.2 & .gimp-2.4 directories in my home folder, and that seemed to fix it.

---

### Post by Spelley on 2007-11-04
I take it back. It worked once, allowing me to print. The dialogue crashes again the next time I try. Something wrong with the settings that get saved.

---

### Post by silbar on 2008-03-22
I don't know if this helps.  In the upgrade to Gutsy from Dapper I lost the ability to print from the GIMP (now version 2.4).  I only tried printing to my HP-5MP printer, and it always complained about not being able to find the printer class.  And, deleting the old .gimp-2.2 directory did not change things.  However, tonight I noticed that there was ANOTHER option in the print setup page called "printer".  Using that, I now CAN printer (to the HP-5MP) from GIMP, albeit kind of slowly.

   Dick Silbar

---

