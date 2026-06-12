---
title: "Integrating source software with repos"
date: 2007-04-10
forum: General Help
---

### Post by UltraMathMan on 2007-04-10
I was running into some strange problems with cups [_encryption errors_]("http://ubuntuforums.org/showthread.php?t=376945") which I managed to resolve by compiling cups 1.2.10 from source. Now however when I try to install something cups dependent with aptitude it still wants to install the cups package from the repos. Is there anyway to "register" the compiled package with aptitude so that it replaces the standard cups package? Thanks.

EDIT: I installed cups with sudo checkinstall -D, which created and installed a debian package.

---

### Post by energiya on 2007-04-11
try
> 
man aptitude

It involves a little reading, but hey! this could be usefull ;)

P.S. I'm not on Ubuntu now, so can't tell you the exact thing, but I'm sure I read it somehere in the man page.

---

### Post by UltraMathMan on 2007-04-11
Yeah, who knew actually reading documentation might help...:oops: I'll definitely go through it and get back to you.

---

### Post by pingpongboss on 2007-04-11
have you tried Force Version under Synaptic's Package menu?

---

### Post by UltraMathMan on 2007-04-11
Suppose I should have mentioned this but I'm running server 6.10, and would rather not install a gui (cupsys is a dependency for gnome and xfce - not sure about kde, so that wouldn't help anyway). Think I might have found something in aptitude's man file > markauto, unmarkauto
	      Mark packages as automatically installed or manually  installed,
	      respectively.  You may specify packages using the same syntax as
	      before, including  specifying  actions  to  be  performed.   For
	      instance, "aptitude markauto '~slibs'" will mark all packages in
	      the "libs" section as automatically installed. so I guess I will give that a try...

---

### Post by UltraMathMan on 2007-04-11
Tried using ```
sudo aptitude unmarkauto cupsys
``` but it's still listed as uninstalled and as a dependency for other packages. The version of cups I installed is listed under ```
aptitude search cups
``` as *cups* not *cupsys*, so perhaps this is the problem? I want aptitude to replace the cupsys package (not installed) with the manually installed cups package. Will keep looking - thanks for any and all help!

EDIT: This might be a bug: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=372184](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=372184)

---

### Post by pingpongboss on 2007-04-11
when you install a package using checkinstall, you have the option of changing the package name. Just don't press ENTER too fast and it'll give you a numbered list of properties of the just-made package that you can change. I'd think that you could name your package cupsys to replace the feisty version.

You'd also need to force that version to not upgrade. Although i have not tried this before, there is a "hold" function in aptitude. Maybe try ```
sudo aptitude hold cupsys
``` after you install it with checkinstall

---

### Post by UltraMathMan on 2007-04-11
Thanks, I'll give it a go!

---

### Post by UltraMathMan on 2007-04-11
Thanks pingpongboss, that did the trick! :popcorn:

---

### Post by pingpongboss on 2007-04-11
glad i could help :D

---

