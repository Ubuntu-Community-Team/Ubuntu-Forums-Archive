---
title: "Alsa config file?"
date: 2007-01-21
forum: General Help
---

### Post by PetePete on 2007-01-21
is there an ALSA config file which i can backup for when my sound mysteriously decides to f' up?!

just had to re-install alsa, would be much quicker if i had a backed up config file, or could booted into Live CD and copied settings etc

thanks

---

### Post by PetePete on 2007-01-22
common guys!
there must be some file(s) somewhere which stores all of ASLA's settings, and someone here MUST know where it is! :D 

ps please dont make me grep my whole drive for it :P

---

### Post by Jessard on 2007-02-10
That's a *very* good question! Heh, I was thinking of brute-forcing a search of the whole drive, too, when I didn't see anything in /etc and ALSA was complaining about illogical settings, but then the first few lines of [this page]("http://phaeronix.net/asoundrc") explained what was going on.

Supposedly /etc/asound.conf is the global ALSA config file (though I suppose it's optional, eh?), but there is also a pair of config files in your home directory: ".asoundrc" and ".asoundrc.asoundconf". (Note the dots, you know, hidden and all that.) My problem was that ALSA had gotten all confused by me replacing a sound device and I had no idea how to "reset" it. In my case, wiping out the config files set everything right. It didn't recreate the files, which confuses me, but I'm not going to argue :) I guess it's already "too late" for you, but hopefully that'll help if it comes up in the future.

---

### Post by ducttapeandzipties on 2007-02-24
I had problems with sound in flash videos, or lack thereof.  If I ran firefox from a term window the errors appeared as if I didn't have alsa installed although I knew I did.  Turns out I had the same problem here... no .asoundrc !  the generic .asoundrc worked for me Thanks!

---

### Post by kjkrum on 2007-10-05
Where did you get it?  I don't have one, either.  I'm also missing my entire /etc/alsa tree.

---

### Post by PetePete on 2007-10-07
check out ~/.asoundrc.asoundconf and ~/.asoundrc

---

