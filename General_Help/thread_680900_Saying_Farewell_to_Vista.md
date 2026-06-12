---
title: "Saying Farewell to Vista"
date: 2008-01-28
forum: General Help
---

### Post by Sugz on 2008-01-28
Ok so here is the situation.
My friend and I are thinking of Replacing Vista on both our Laptops with Ubuntu as the Primary OS.
I will probably use VMware later to use XP but ill leave that for now.
So We are both using Wubi to run Ubuntu Feisty.

I am doing this because Vista is wasted space, i just dont use it on my Laptop and i would prefer it if it was gone.

Im not sure about them but myself, i have just spent a ages getting my Ubuntu installation to the way i like it.
But my friend is willing to wipe out Vista and just have Ubuntu.

So how would we go about doing this cleanly?

1. Uninstall Vista
2. Install Ubuntu?
*3. Keep current Ubuntu Setup

Any help will be appreciated.
-Sugz

---

### Post by steveneddy on 2008-01-28
Is this a second thread?

I just posted on a thread exactly like this a few minutes ago.

[Here is the original thread.]("http://ubuntuforums.org/showthread.php?t=680893")

You only need one thread, dude.

---

### Post by mocoloco on 2008-01-28
There's no need to "uninstall" Vista, you'll just wipe it out one way or another.  There are a number of options for you.  The question is, how much info do you have that you care about?  Pretty much everything you need should be in your home folder.  You could
1) Backup all the data from /home to an external source, then do a fresh install that takes over the entire drive, create a user (or users) with the same name(s) and drop in your same /home data.
2) Create a new partition for your /home folder, move everything there, then do a fresh install, doing manual partition configuration and set /home to use the new partition.
3) Follow [wubi's process]("http://ubuntuforums.org/showthread.php?t=438591") to install it to it's own partition, then wipe out your vista partition.

---

### Post by mocoloco on 2008-01-28
Didn't see this was a double-post.  In that case let this one die, as the other has more momentum.  Yeah, in the future don't post twice, even if the issue applies to more than one category.  It just makes a mess of things in the long run.

---

