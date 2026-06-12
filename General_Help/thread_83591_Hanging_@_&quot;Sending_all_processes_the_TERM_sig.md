---
title: "Hanging @ &quot;Sending all processes the TERM signal...&quot;"
date: 2005-10-29
forum: General Help
---

### Post by Doc.Caliban on 2005-10-29
Following nVidia's instructions, and a few posts in the forum, I changed my init state from the default "2" to "1" so I could boot without loading the GUI.

Now my system hangs during startup at:

"Sending all processes the TERM signal..."

I'm 24 hours into my first linux use ever, so I'm totally new at this.  Will booting into recovery mode allow me to edit the inittab file again so I can at least get back to where I started?

-Doc

---

### Post by matthewv on 2005-10-29
[QUOTE=Doc.Caliban]Following nVidia's instructions, and a few posts in the forum, I changed my init state from the default "2" to "1" so I could boot without loading the GUI.

Now my system hangs during startup at:

"Sending all processes the TERM signal..."

I'm 24 hours into my first linux use ever, so I'm totally new at this.  Will booting into recovery mode allow me to edit the inittab file again so I can at least get back to where I started?

-Doc[/QUOTE]
During startup???? Isn't "Sending all processes the TERM signal..." at shutdown

---

### Post by Trab on 2005-10-29
where did you edit this file?
u might need to use a live-cd... dunno if recovery mode will work...
my advice to a newbie to linux: dont mess around with stuff that keeps it from starting up :-D
and, sending all prcoesses the term signal should be at shutdown...
term is for terminate.... get it?

---

### Post by Doc.Caliban on 2005-10-29
That's what all the threads I could find said, yes.  But this is during boot.  

-Doc

---

### Post by matthewv on 2005-10-29
To change the default runlevel you edited your /etc/inittab file. Easiest way to fix it (put it back to how it was) is to boot the ubuntu live cd (or any other linux live cd) and mount your hd, and then change the file back to how it was before you played with it. :) If booting recovery mode works, just type ```
 nano /etc/inittab 
``` to edit the file

---

### Post by Doc.Caliban on 2005-10-29
OK, let's start over.

I am new to linux.  I am not anywhere near being new to computers and tinkering around in the deepest bits of an OS.  

The default init for Ubuntu is 2.   I changed it to 1 because that's supposed to boot it without loading the GUI. 

Now when I boot, (that's the starty-upy part, right?) it goes through it's process and about half way through the last few lines when it hangs are:

Initializing random number generator...          OK
Setting up X server socket directory...       OK
Setting up ICE socket directory...              OK
Sending all processes the TERM signal...

And there it sits.

-Doc

---

### Post by Doc.Caliban on 2005-10-29
[QUOTE=matthewv]To change the default runlevel you edited your /etc/inittab file. Easiest way to fix it (put it back to how it was) is to boot the ubuntu live cd (or any other linux live cd) and mount your hd, and then change the file back to how it was before you played with it. :) If booting recovery mode works, just type ```
 nano /etc/inittab 
``` to edit the file[/QUOTE]


That's what I was wanting to try, but I didn't know exactly what recovery mode is so I didn't want to do it yet.

I have a live CD of a different version of linux, if that will still work, then I'll do that.

However, I still want to do this so I can install the latest nVidia driver, so how do I boot to a prompt?

Thanks,

-Doc

---

### Post by Doc.Caliban on 2005-10-29
Recovery mode got me to a prompt.   Why won't "normal" mode?

Is recovery mode an OK place to install a video driver from?  If so, problem not solved, but workaround found.  Good enough for now.

-Doc

---

### Post by matthewv on 2005-10-29
Recovery mode, if it works, will boot you up to a root prompt. It will not start X. If that's what you need, great.

EDIT:
Sorry, you beat me to it. I honestly don't know if it's a good idea to install drivers from the recovery prompt.

---

### Post by Doc.Caliban on 2005-10-29
[QUOTE=matthewv]Recovery mode, if it works, will boot you up to a root prompt. It will not start X. If that's what you need, great.

EDIT:
Sorry, you beat me to it. I honestly don't know if it's a good idea to install drivers from the recovery prompt.[/QUOTE]


Hey, I appreciate the help.

So I changed it back to 2 and then typed "reboot" and watched it send the TERM signal without hanging, and now I'm back in GNOME.  

I do need to figure this out though so I can do my video driver update verbatim to nVidia's instructions.  Something is obviously causing it to send the term command during startup.  Why that hangs is another thing as well.

-Doc

---

### Post by Doc.Caliban on 2005-10-29
You know what would work for me, is just being able to shut down x and end up at a prompt.   So there's my real newbie question for the night.

---

### Post by Doc.Caliban on 2005-10-29
Is there a better forum to be asking these questions in?  A place where people really know the startup process in depth enough to help me figure out the original problem?  When I did tech support for a big software company several years ago, we would have jumped all over something like that.  The weirder the problem the better.  Workarounds were not considered fixes.

-Doc

---

