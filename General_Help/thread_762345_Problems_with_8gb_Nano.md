---
title: "Problems with 8gb Nano"
date: 2008-04-22
forum: General Help
---

### Post by ljoslin on 2008-04-22
I got a new Nano today and have been having some issues.

Everything seems to go normally, plug it in, rhythmbox opens up, I drag and drop my music, everything seems cool.  Then I eject the Ipod and unplug it.  The IPOD still says "No Music"?!?!  I have followed a few HowTos to no avail.  I plugged the IPOD into my laptop, and searched the mount point and could find all the music, so I know everything is on the IPOD!  Any Ideas?  I'm running Ubuntu Gutsy, have tried gtkpod as well with same results, so any help would be great!  Thanks!

-=ljoslin=-

---

### Post by BandD on 2008-04-22
Apple has added a kind of 'protected' database in newer ipod models.  Basically, the apple firmware checks to make sure the database meets some secret hash and if the hash doesn't work, then the firmware thinks the ipod is compromised and will refuse to touch the files that ARE ON THE IPOD.  Basically it thinks it has cooties and ceases to function.  Apple says it is to improve stability or some such...

You can try using gtkpod instead, or updating to a newer version of Rhythmbox and whichever tool Rhythmbox uses to interface with ipods (I'm not really sure what that is).  

Also try googling for 3rd gen nanos (the shorter fatter one) and linux, there should be a lot of documentation out there.  The only bummer is that you may have to use itunes to reset the database.  But I'm not sure.  

Good luck!

---

### Post by ljoslin on 2008-04-26
I upgraded to hardy and all is well now?!

-=Larry=-

---

