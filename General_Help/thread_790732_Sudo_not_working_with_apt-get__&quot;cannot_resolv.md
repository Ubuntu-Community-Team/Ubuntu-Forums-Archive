---
title: "Sudo not working with apt-get:  &quot;cannot resolve host&quot; error"
date: 2008-05-11
forum: General Help
---

### Post by mjpatey on 2008-05-11
I hope I describe this accurately, as I'm at work right now, and not at my Ubuntu computer...

I can't seem to install packages right now.  Other "sudo" activities seem to work fine, but when I try to sudo apt-get install something, I get an error that says something like:

> "sudo: cannot resolve host Shekkster" (the hostname of my computer)Similarly, when I try to install something via Synaptic, once the package(s) are selected, I click "Apply", and Synaptic keeps trying and trying (for hours, even... I let it go overnight and it was still showing the "working" cursor in the morning).

A little background may help...

This computer was initially part of the Windows network in my home (MSHOME), with 2 other computers.  I just had to re-install Windows on one of the other computers, and instead of naming the new Windows install's network "MSHOME" I changed it to our family's last name.  I don't know yet how our third computer is handling this change, as it hasn't been used since the change.

So, is it possible that my computer is now known as "Shekkster@<newnetworkname>" and that's why sudo is unable to allow me to run apt-get or Synaptic?  If that's the case, how do I make things right again?

A quick apology/disclaimer:  the error message "sudo: cannot resolve host Shekkster" is an approximation on my part, from memory.  The word may not be "resolve" but it's something to that effect.

Thanks for any insight you may be able to provide!

-Mark

---

### Post by Monicker on 2008-05-11
Known bug:

Check here for how to fix it.

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

---

### Post by mjpatey on 2008-05-11
Woohoo!  Thanks a lot!!!  I'll try that as soon as I get home tonight.  :-)  For those referencing this thread in the future, the relevant link to fix this problem is:

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

In the example fix given by the forum staff member, the O.P's hostname is used ("
icarus-laptop").  Just replace that with your computer's hostname, and all should be well and dandy!

-Mark

---

