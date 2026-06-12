---
title: "firebug no longer works in Firefox"
date: 2007-03-05
forum: General Help
---

### Post by sdhoigt on 2007-03-05
I'm not sure when, but from Firefox 2.0.0.1 on the Firebug extension stopped working.  F12 doesn't do anything anymore; even if I try to 'Open Firebug' via Tools->Firebug, that doesn't work either.

Currently running Firefox 2.0.0.2
Kubuntu Edgy Eft/6.10
Firebug 1.01

Any ideas are appreciated.

Thanks,
SD

---

### Post by sdhoigt on 2007-03-06
So I moved my ~/.mozilla directory away, and restarted Firefox with a clean palette.  I install Firebug, restart FF and Firebug works.  Good.  Kinda what I had hoped.

So it must be a problem somewhere in my ~/.mozilla dir.  

Anyway, I move my old .mozilla dir back (after deleting the newly created .mozilla) to retain my settings, start-up Firefox and Firebug works!  Makes absolutely no sense, but I'm happy.

Seriously.  Here is my command line history to prove I ain't nuts.
  497  mv .mozilla .mozilla.bak		(move the dir away)
  498  firefox				(run Firefox)
  499  rm -rf .mozilla			(blow away newly created dir)
  500  mv .mozilla.bak/ .mozilla	(move back old stuff)

See ya.

---

