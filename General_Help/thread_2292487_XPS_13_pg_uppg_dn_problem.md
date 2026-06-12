---
title: "XPS 13 pg up/pg dn problem"
date: 2015-08-28
forum: General Help
---

### Post by mehnertc on 2015-08-28
I recently purchased a used 2012 Dell XPS 13 (l321x), and installed 14.04.  Everything is working fine, except for the pg dn, pg up, home, and end (FN plus appropriate arrow key).  When I try to use this, it will sometimes work (one time in ten), but most of the time, regardless of which (pg dn, for example), it goes to the bottom of the page, and then becomes unuseable.  Touchpad becomes unresponsive after this.  Reboot fixes it. This happens on all applications, including Chrome, Libreoffice, etc.

 FWIW, I am a noob, so pretend you're talking to a 5th grader...  ;)

Thanks, in advance

See post #6 below for additional information.

Edit: Confirmed that it is not a hardware issue.  External Bluetooth keyboard exhibits same problem.

---

### Post by ajgreeny on 2015-08-28
As it does work sometimes, even if only once in ten times, it sounds like a hardware problem.

Is it in Chrome only that you see this problem or all applications?  If just in Chrome I am afraid I can not help as I've never used that browser.

---

### Post by mehnertc on 2015-08-28
I've done a little testing.  While it worked a once, just after installing 14.04, now it seldom works.  As soon as I hit FN+down arrow, it goes to the bottom of the page, instead of page down.  Then the touch pad won't work anymore, either.  Reboot fixes the issue.  Doesn't matter whether it's in a browser or a document.  Same behavior.  Thanks for your response.

---

### Post by ajgreeny on 2015-08-28
But you didn't answer my question; just Chrome or all applications?

---

### Post by mehnertc on 2015-08-28
All applications.  FWIW: I doubt it's a hardware issue as arrow up and arrow down keys work fine.  It's only FN+arrow up, down, left, or right (i.e. page down, page up, end, and home) that cause a problem.

Edit: I just tested with an external Bluetooth keyboard, and confirmed the same issue exists as described in the OP.

---

### Post by mehnertc on 2015-08-29
I have installed, and run EVTEST.

I get intermittent, correct response occasionally.  But most times I get a panic (?) results, for pg dn, pg up, home, end.  

For example, when responding correctly to pg dn, I get:

"Event: time 1440844964.051430, type 1 (EV_KEY), code 109 (KEY_PAGEDOWN), value 1"

But the next time I try it, I get:

^[[6~ ^ ^[[6~ ^^[[6~ ^^[[6~ ^  ..........          repeated endlessly.

Any guidance at all appreciated.  SWAGs welcome.

---

### Post by mehnertc on 2015-08-29
Well, the solution appears to have been pretty simple.  In System Settings/Keyboard/Typing/Repeat Keys, uncheck "key presses repeat when key is held down".

---

### Post by ajgreeny on 2015-08-29
Well, I'm very happy that you have solved this problem, but I think this must be hardware related as I think the repeat setting that you did have is the default, and I have never heard of it causing that problem before.

It is certainly the default on my Xubuntu system and the OSs I have installed in VBox.

---

### Post by mehnertc on 2015-08-29
> **ajgreeny said:**
> Well, I'm very happy that you have solved this problem, but I think this must be hardware related as I think the repeat setting that you did have is the default, and I have never heard of it causing that problem before.

It is certainly the default on my Xubuntu system and the OSs I have installed in VBox.
 
I already did use the thread tools to mark it as Solved.  But how can it be a hardware problem when the problem still manifests while using a Bluetooth external keyboard?

---

