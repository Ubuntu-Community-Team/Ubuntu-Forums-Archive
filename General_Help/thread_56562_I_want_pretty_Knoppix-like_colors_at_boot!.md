---
title: "I want pretty Knoppix-like colors at boot!"
date: 2005-08-13
forum: General Help
---

### Post by One Quick Question on 2005-08-13
Ok, this has got to be the most non-essential thing on my tray right now, but since I've been looking at the bootup messages alot in experiments to trim down the init scripts, I've got to know this.
In Knoppix (and perhaps other distros) when it boots up, all the messages are in [pretty colors](http://shots.osdir.com/slideshows/slideshow.php?release=376&slide=2).   Can I apply those to my Ubunut startup too?
I don't have a Knoppix CD handy to look through things in /etc/ myself, even if I knew what I was looking for.
And Googling for "knoppix boot OR start colors" or such just won't cut it.

Any ideas?

---

### Post by jeremy on 2005-08-13
[http://ubuntuforums.org/showthread.php?t=50054](http://ubuntuforums.org/showthread.php?t=50054) has what you are looking for.

---

### Post by matthew on 2005-08-13
[QUOTE=jeremy][http://ubuntuforums.org/showthread.php?t=50054](http://ubuntuforums.org/showthread.php?t=50054) has what you are looking for.[/QUOTE]
I participated in that thread...cool stuff, but it isn't as complete as what I think OP is looking for if you look at the linked [screenshot](http://shots.osdir.com/slideshows/slideshow.php?release=376&slide=2)

I love the look of the Knoppix boot messages and would love to have the same thing in Ubuntu.

---

### Post by void_false on 2005-08-13
Ah... Fluxbox on Knoppix 4.0 is so sweet. :) 

Sorry for offtopic.

---

### Post by Lord Illidan on 2005-08-13
I don't get it.. you want a bunch of rainbow colours?? You want to see the terminal messages??
 And here are the splashy people doing their best to cover it up, lol..

---

### Post by void_false on 2005-08-13
[QUOTE=Lord Illidan]I don't get it.. you want a bunch of rainbow colours?? You want to see the terminal messages??
 And here are the splashy people doing their best to cover it up, lol..[/QUOTE]

Linux is freedom of choise. Personally I prefer terminal messages with rainbow colors instead of splash image with progress bar. IMHO it is too windowish.  :---)

---

### Post by matthew on 2005-08-13
[QUOTE=Lord Illidan]I don't get it.. you want a bunch of rainbow colours?? You want to see the terminal messages??
 And here are the splashy people doing their best to cover it up, lol..[/QUOTE]
I like to see/know what is happening all the time so this would let me continue to do so and look nice at the same time. It would scare my parents, though so splashy would be better for them...and I would imagine they are in the majority.

---

### Post by One Quick Question on 2005-08-13
Thanks for all the replies!
Yeah, a slashy screen covering up all the interesting output isn't want I'm after.
The green [ ok ]'s are nice though!

Is there a way I can have. say, the rest of the text blue?  I'm looking in the init-functions file and I can't figure out where I would put such a thing.  I don't spy an "echo thingthatweredoing" line...    I'll experiment all over the place a bit later when I can init 1. 
And after that, where can I tell which init script thing it running at the time?
It would be so cool to write something that, for example, makes the system checks in blue, hard drive journal checks in cyan, and the daemons in yellow.  Or something like that!  That would be awesome!

---

### Post by matthew on 2005-08-14
I don't have time right now to play around with it any more than I already have to try to figure out how to do this. Maybe someone else will have an idea. If not, I'll try to revisit this when I have some free time, perhaps by looking at the Knoppix /boot/grub/menu.lst or grub.conf or whatever it is using and try to adapt it... No promises as to when/if I will be able to get to this, though, so if someone is able to do so first that would be quite welcome.

---

### Post by One Quick Question on 2005-08-14
I've been going through /etc/init.d/ and editing all the scripts to output some color using the same method as the green [COLOR=Green]ok[/COLOR]'s.  It's pretty tedious, but I guess it works.

edit:
By the way, I found some funny (to me) comments in the apache2 init script:
Under the "# if we are here something is broken" else:
```

   #   this is the worst situation... just kill all of them
   #for i in $PIDS; do
   #   kill $i
   #done
   #   Except, we can't do that, because it's very, very bad

```
hehehe

---

