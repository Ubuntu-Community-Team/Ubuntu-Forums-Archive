---
title: "reopened Thread: Kolour paint 4, deleted or closed color palette"
date: 2014-11-07
forum: General Help
---

### Post by treaki on 2014-11-07
hi,

i had the same problem in debian which  				 				 					 						 	[**[COLOR=#000000]dude1[/COLOR]**]("http://ubuntuforums.org/member.php?u=1489219") described in his or her thread "Kolour paint 4, deleted or closed color palette" ( [http://ubuntuforums.org/showthread.php?t=1897290](http://ubuntuforums.org/showthread.php?t=1897290) ). Unfortunately this thread was closed what i wouldn't consider as a good practice...

Its looked like a bug, if you detach the color pallet and than close that window there is no way how it can be opened again. This state get saved and reloaded so youve got a problem. Ive solved that problem by closing all instances of kolourpaint, deleting the file ~/.kde/share/config/kolourpaintrc and starting kolourpaint again. This woldnt be done by reinstalling of cause because it is a user side thing which will not be handled by dpkg by definition...

I guess i will create a bug record for that problem, probably it will get fixed.

greetings treaki

---

