---
title: "Latin American keyboard layout bug..."
date: 2005-10-27
forum: General Help
---

### Post by Juanra on 2005-10-27
Hi all, hope all of you are fine.
I found something weird in the Ubuntu Breezy Badger 5.10, when you finish installation and the GDM starts, its impossible to write a word in the login user input with a [COLOR="Red"]**latin american keyboard layout**[/COLOR], and its happening with other **[COLOR="Red"]sp[/COLOR][COLOR="Orange"]ani[/COLOR][COLOR="Red"]sh[/COLOR]** keyboard layouts too.

To fix it you have to go to xorg.conf file and change the layout to "en" for example.

I read one [thread talking]("http://www.ubuntuforums.org/showthread.php?t=64982&highlight=latin+american") about the same bug but nobody helped the owner.  I would like to know if any of you could help me with this, or know how i could fix it, cuz' I'm really needing some characters in the "latin american/spanish keyboard layout".

Thanks a lot for all the time given to read this.

---

### Post by tagbre on 2005-10-27
This was a problem in Breezy Preview, but afaik it's been fixed in the final release, at least I didn't have the problem when I upgraded to final version. Anyway, if u still didn't do the upgrade u can fix it really easily by editing xorg.conf: just change "la" for "latam"

---

### Post by Juanra on 2005-10-27
[QUOTE=tagbre]This was a problem in Breezy Preview, but afaik it's been fixed in the final release, at least I didn't have the problem when I upgraded to final version. Anyway, if u still didn't do the upgrade u can fix it really easily by editing xorg.conf: just change "la" for "latam"[/QUOTE]

Well, I downloaded the .iso from the ubuntu site the last week. I thought that was the final release.  I'm going to try the "latam" change [COLOR="Red"]**tagbre**[/COLOR], and thank you so much for your quick reply.

Anything, Anytime,

Juanra

---

