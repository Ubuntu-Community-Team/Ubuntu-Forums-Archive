---
title: "Mount .ISO Gnome launcher"
date: 2007-02-08
forum: General Help
---

### Post by ed_agamemnon on 2007-02-08
Every time I play Starcraft, I go through the following (tedious) routine:

```

cd /home/<>/.wine/drive_c/Program Files/Starcraft
sudo mount -o loop StarcraftCD.iso /SCmount
nice -n 20 wine starcraft.exe

```

I've tried scripting this set of commands as a .sh, but this doesn't enable me to launch Starcraft from the desktop. I don't know why.

What I'd really like to be able to do is have a button that:
1) mounts my starcraft.iso
2) launches Starcraft with nice and wine
3) unmounts the .iso when I'm done.

Whatever attempts at this I have made have failed - even making three seperate buttons for each of the above tasks. Why does Create New Launcher -> Command: gksudo mount -o loop etc. etc. fail?

So the question is, how can i mount a .iso from a launcher on the desktop?

---

### Post by nereid on 2007-02-08
I think gksudo has a problem with the -o parameter (it thinks, that it applies to itself instead to the mount command). So I would do it like this

```

#!/bin/bash
cd /home/<>/.wine/drive_c/Program Files/Starcraft
gksudo "mount -o loop StarcraftCD.iso /SCmount"
nice -n 20 wine starcraft.exe

```

To mount and to launch the game. After you've finished playing a
```

#!/bin/bash
gksudo umount /SCmount

```

should do the job.

---

### Post by ed_agamemnon on 2007-02-12
thanks! i'll give it a go when i get home...

---

