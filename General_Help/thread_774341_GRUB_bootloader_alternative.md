---
title: "GRUB bootloader alternative?"
date: 2008-04-29
forum: General Help
---

### Post by Zorael on 2008-04-29
I'm looking for something to replace GRUB with, as bootloader.

The system in question is going to be a family computer, so I'm basically looking for something easy on the eyes.  Which rules out GRUB's "loading stage1.5", which seems to me to be more of a debug message and shouldn't be displayed on normal end-user builds. The more graphical the better. :>

What options are there? Any advice?


edit: nuh, misspelled bootloader tag

---

### Post by Jimmey on 2008-04-29
You can set the grub timeout to .5 seconds so that it doesn't show.
Alternatively, you can add a grub splash or add some colours to it, to make it prettier. Here's an example:
[img]http://www.elblogdemaverick.com/uploads/ubugrey.png[/img]

Or you could try Lilo as an alternative boot manager.

---

### Post by sujoy on 2008-04-29
> Or you could try Lilo as an alternative boot manager.

yes but i agree more with your previous solution. a splash works wonders, also lilo seems more like '70s to me

---

### Post by Zorael on 2008-04-29
Interesting; do elaborate. To my knowledge, grub splashes were simply low-res low-color images displayed behind the normal grub screen? Is there a guide someplace?

---

### Post by sujoy on 2008-04-29
yes there is, :)

[http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341)

---

### Post by Zorael on 2008-04-29
That's the low-res low-color background splash, no? The one that will end up looking like this.
[img]http://schragehome.de/splash/tenerife.png[/img]

I'm more interested in Jimmey's example; it doesn't look like grub at all.

... *IS* that even grub at all?

---

### Post by sujoy on 2008-04-29
yes its grub, its configured that way by default in linux mint, i am looking for a guide to that (i use the plain text version myself)

---

### Post by sujoy on 2008-04-29
found a guide you might be interested in, take a look here,

[http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/]("http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/")

---

### Post by Zorael on 2008-04-29
> **sujoy said:**
> found a guide you might be interested in, take a look here,

[http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/]("http://tuxenclave.wordpress.com/2008/01/18/how-to-install-gfx-grub-in-ubuntu/")
Awesome, worked like a charm, many thanks.

Now to find some more themes. :>

---

