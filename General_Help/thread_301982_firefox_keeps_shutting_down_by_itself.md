---
title: "firefox keeps shutting down by itself"
date: 2006-11-17
forum: General Help
---

### Post by evereign on 2006-11-17
Hey guys,

My Firefox has been starting to act crazy. For no reason at some points it will close by itself immediately after I click on a link. And I figured out that it's not the link itself because I would go back and try the same link and it would open it. As far as I can tell it is completely random. Do you know what I could do?

Thanks in advance!

---

### Post by evereign on 2006-11-17
Oh and btw,

I opened firefox from a terminal and watched for what it would say when this random closing happens.
This is what it says:

Segmentation fault


I hope that helps narrowing where the problem starts. 

Thanks again.

---

### Post by Gotterdammerung on 2006-11-18
same dreadful problem here.

---

### Post by bollix47 on 2006-11-18
Have a look [here]("http://kb.mozillazine.org/Firefox_crashes") to see if any apply to your situation.

---

### Post by Cyfr on 2006-11-22
I have this problem too and it effects aMSN also. aMSN will just randomly close as will firefox.

---

### Post by Luke1972 on 2006-12-05
I'm using Breezy with FF 1.5.0.8 and am having the same problems.  I've tried starting in safe mode, with a new profile, re-installing FF, without extensions but still get the same problem (if I run it from the command line I too get Segmentation Fault).  Also I've tried the Pango fix ([http://www.ubuntuforums.org/showthread.php?t=52875](http://www.ubuntuforums.org/showthread.php?t=52875)) and that didn't work.   Any suggestions?  Please?

---

### Post by Luke1972 on 2006-12-05
Actually I tried to do the Pango fix but don't have the pbgo lines to comment out, just this:

> 
if [ "x${MOZ_DISABLE_PANGO}" = x ]; then
    if egrep '^(bn|gu|hi|kn|ml|mr|ne|pa|ta|te)_' \
	/var/lib/locales/supported.d/*[^~] >/dev/null 2>&1; then
	MOZ_DISABLE_PANGO=0
    else
	MOZ_DISABLE_PANGO=1
    fi
    export MOZ_DISABLE_PANGO

---

### Post by Gotou on 2006-12-08
Mine won't even start.

Running Ubuntu 6.06 and Fluxbox.  Tried it in Gnome, won't start there either.

Tried using the terminal to see any error messages.  All I get is

$firefox
Segmentation fault

Firefox was working fine yesterday morning.  Did a synaptic update and then Firefox stopped working when I tried to use it later that night.  Don't remember what Synaptic changed.](*,) 

Loaded a couple other browsers, but Firefox is my favorite and of course has all my bookmarks.

I'll look into the pango thread.  It doesn't seem to fix things for some users.  Hopefully there will be a Synaptic update that fixes this.

<sigh>

---

### Post by Gotou on 2006-12-08
Got it to work!:-D

I don't know if this will work for everybody but here's what I did.

Downloaded and installed the latest version (Firefox 2.0)from the Mozilla website.
[http://www.mozilla.com/en-US/](http://www.mozilla.com/en-US/)

Simple enough for me, which is good. <breathes a sigh of relief>

I was having BSOD flashbacks <shudders>

---

### Post by Luke1972 on 2006-12-18
Ok I solved this but I did 3 things at once so I don't know which one actually did it and which weren't needed.   I used synaptic to reinstall libcairo2 and libcairo2 dev, then re-installed libpango1 and libpango1 common, then I reinstall all flashplayers (but it was working normally on websites using flash and crashing on a plain and boring login plae so I don't think that was essential but various people had said try that to me.  

Hopefully that might help someone.

---

