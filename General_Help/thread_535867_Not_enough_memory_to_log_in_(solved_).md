---
title: "Not enough memory to log in? (solved )"
date: 2007-08-27
forum: General Help
---

### Post by salambander on 2007-08-27
Right. So you've installed Ubuntu and downloaded lots of lovely free software and put all your music in to play on Amarok or XMMS. Then... the desktop freezes. You panic. You turn it off. You turn it on again. Everything seems fine until you log in - an error message pops up. "Not enough memory to log in". AAAGH!

It's happened to me twice now, and there's one way to fix it that works well for me:
1. When you boot, press Esc and switch to recovery mode. The whole window will look like the terminal.When in this mode, use the following commands to explore and delete as many files and folders as you can (that you don't need). Stick to your home folder - don't mess with bin or usr/bin or any of those if you're not sure what you're doing. 
[B]
 ls[/B] to see what directories and files are available
** cd "DIRECTORYNAME"** to get into the directory
** cd ../  ** to go back
 **rm -rf "filename"** to delete files or directories

Get rid of as much as you can, big things like .pdfs,music, movies and pictures. This is a good time to spring clean your music collection.

When you feel like you've done enough (you need to do about 20MB worth, I think), reboot and you should be able to log in.  If not, lather, rinse and repeat.

To stop this from happening again, maybe put some of your less-accessed files onto an external hard drive or flash disk, and delete programs you don't use (but downloaded cos they looked cool), Be ruthless. Pick your favourite music player and completely remove the rest. Get rid of duplicate photos (or photos so similar they might as well be duplicates). Do as much as you can and hopefully it won't happen again.

---

### Post by SPr on 2007-08-27
Did this really cure the problem or was it just co-incidence?

Rather than risk damaging the PC by hitting the power button use the tips here: [www.arsgeek.com/?p=787](www.arsgeek.com/?p=787)

---

### Post by salambander on 2007-08-27
Well, it solved the problem of not being able to log in, and the fact that it worked twice rules out coincidence. But thanks for the link!

---

### Post by SPr on 2007-08-27
> **salambander said:**
> Well, it solved the problem of not being able to log in, and the fact that it worked twice rules out coincidence

Fair enough.

> **salambander said:**
> But thanks for the link!


You're welcome.

---

