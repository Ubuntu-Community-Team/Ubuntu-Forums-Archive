---
title: "gdesklets help"
date: 2004-10-31
forum: General Help
---

### Post by brschmid on 2004-10-31
under applications>accessories>gdesklets
when i do that it wont load 

but if i type gdesklets from a terminal window i can get it to run.

why???

---

### Post by Rancoras on 2004-10-31
Try this thread:
[http://ubuntuforums.org/showthread.php?t=1851](http://ubuntuforums.org/showthread.php?t=1851)

---

### Post by brschmid on 2004-10-31
[QUOTE=Rancoras]Try this thread:
[http://ubuntuforums.org/showthread.php?t=1851](http://ubuntuforums.org/showthread.php?t=1851)[/QUOTE]
 you gave me that link before. 

how is that any different than what i am describing?

edit: now i get errors that i don't have sensors loaded :(

---

### Post by jdusablon on 2004-10-31
I agree. That thread is pointed to for all gdesklets problems, but it doesn't actually explain what to do to get rid of the "failed authentication" problem.

I can't get either GUI or teminal gdesklets to work. Is this a package version problem?? Which packages do those of us who are having the problem need?

Also, PLEASE USE %$#@ CODE TAGS!!!! Especially moderators, who probably should know better. No offence intended, love Ubuntu, love this forum.

---

### Post by Rancoras on 2004-10-31
[QUOTE=brschmid]you gave me that link before. 

how is that any different than what i am describing?[/QUOTE]

According to what you described, that should have helped.  I'm sorry if it didn't.


[QUOTE=jdusablon]I agree. That thread is pointed to for all gdesklets problems, but it doesn't actually explain what to do to get rid of the "failed authentication" problem.[/QUOTE]

This is the only thread where I find mention of the "failed authentication" problem.  I'm not familiar with that, what is it?

---

### Post by jdusablon on 2004-11-01
Well, in my quest to customize gnome with some fancy eye-candy, I've discovered that I needed to try gdesklets. In synaptic, I select gdesklets and gdesklets-data so that there are some sensors to try out.

Everything goes well on the install, but when I run gdesklets from command, I get this:

```
 # gdesklets

(gDesklets:5242): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
gDesklets 0.26.2
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.

/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)
```

What does this message mean? In the other thread, [http://ubuntuforums.org/showthread.php?t=1851](http://ubuntuforums.org/showthread.php?t=1851) you yourself mention a method of getting gdesklets up and running, but this doesn't seem to work for me.

Do you mean```
gdesklets > run
```because this yields the exact same error as just running ```
gdesklets
```That's what I mean about the code tags. Not using them makes things unclear for newbies like me.

---

### Post by Rancoras on 2004-11-01
Ah, now I see why you mentioned the code tags.  Those aren't code lines, they are menu clicks and such.  Alas, I'm sorry, but I don't write howtos very well.  In the first part of my message, I mean for you to click Applications then click run.  Then type gdesklets in that box and click the "run" button.  With that, I think you can figure the rest out.

---

### Post by jdusablon on 2004-11-01
My apologies! I now have some running. Thank you very much, please forgive my frustration.

Excellent.

---

