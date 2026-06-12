---
title: "x error on login after upgrade from 386 to 686 kernel"
date: 2005-10-17
forum: General Help
---

### Post by bennettg on 2005-10-17
noob here.  frustrating time with breezy.  relied on ubuntuguide for hoary, but no update.

used ubuntuguide to load nvidia drivers for breezy.  after tweaking the system, i downloaded the 686 kernel.  on the next restart i got a blue screen of death type screen telling me x could load.  i do not know how to take a screenshot or save the long file documenting the error, but it said something about not being able to load the nvidia diver or it not being found.
i tried to strat gdm, but it said it was running.

i restarted the computer with 386 and no probs.  restart with 686 kernel and i always get the error.  

can anyone help a noob?  i'd keep the 386 kernel, but the performance wiith 686 is so much better

---

### Post by Dr. Nick on 2005-10-17
Should be an easy fix, Just install Nvidia-glx for the 686 kernel, if you want to get into the 686 kernel edit Xorg.conf back to nv insted of nvidia then try again to get to 686. Basically you need the 686 nvidia packages aswell ,I bet you only have 386 ones

---

### Post by bennettg on 2005-10-17
sorry i am such a noob but can you give me more specific directions on how i can go about that?

thanks in advance

---

### Post by Dr. Nick on 2005-10-17
Sure, its been awhile since Ive done that and apparently they changed naming schemes :) so my instructions would be hard to follow even for me . hehe

From here on out I am assuming your card is newer that a geforce2 if not it will be different.

Ok boot into the 386 kernel so you can boot into a GUI and open synaptic, search for "linux-restricted-modules" thier will be several of them, I assume only one is green meaing  its installed, and I bet it has a -386 at the end of the file name. Select the one with a -686 and install it aswell. Make sure the 2.6.x.x matches the output of ```
uname -a
``` command launched from a terminal, It should be the same name as the one installed just 686 instead of 386. After that is installed try to boot into the 686 one and see if that helps

---

