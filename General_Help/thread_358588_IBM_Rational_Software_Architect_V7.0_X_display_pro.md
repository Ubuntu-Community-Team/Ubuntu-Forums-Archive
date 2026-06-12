---
title: "IBM Rational Software Architect V7.0 X display problems"
date: 2007-02-11
forum: General Help
---

### Post by mdailey on 2007-02-11
Hi,

Has anyone successfully installed IBM Rational Software Architect V7.0 on Ubuntu?

I'm running Edgy, fully updated, with a NVIDIA GeForce 4 display adapter.

With the default X installation and after installing the latest X driver from NVIDIA, I get the same problem.

IBM Rational Software Architect V7.0 installs and runs just fine, but UML diagrams in the diagram window show up only partially or not at all.

Here's a screenshot:

[http://www.cs.ait.ac.th/~mdailey/IBM/Screenshot.png](http://www.cs.ait.ac.th/~mdailey/IBM/Screenshot.png)

The Outline view shows that I'm looking at a perfectly good diagram, and I've selected the little use case oval, but nothing is showing up in the diagram editor window.

I would guess that RSA is using some X extension I don't have for the diagram display.  Any ideas on how to debug this?

Thanks!

---

### Post by Aurorion on 2007-08-05
I know it's been a while, but have you solved this?

Has anyone managed to get RSA v7 working perfectly on Ubuntu?

---

### Post by mdailey on 2007-08-05
Sorry, forgot to post the solution. If you turn off antialiasing in the options menu everything works fine.

I originally found this on developerworks but now I can't find the link.

Good luck!

Matt

---

### Post by Aurorion on 2007-08-06
> **mdailey said:**
> Sorry, forgot to post the solution. If you turn off antialiasing in the options menu everything works fine.

I originally found this on developerworks but now I can't find the link.

Good luck!

Matt

Err... Can you please elaborate? Where options menu? :confused:

Sorry, I have been using RSA for like just 2 weeks now... So not really familiar with all the options...

---

### Post by Aurorion on 2007-08-06
Just solved it!!! :guitar:

[http://www-1.ibm.com/support/docview.wss?uid=swg21256886](http://www-1.ibm.com/support/docview.wss?uid=swg21256886)

> **Problem**
On Linux operating systems, UML artifacts might not be visible in the diagrams where they have been placed. The objects are visible in the outline window and can be double-clicked upon in the diagram although they seem invisible.
 
**Cause**
The problem is due to the anti-aliasing option in the diagram modeling preferences.
 
**Solution**
To resolve the problem, go to Window -> Preferences -> Modeling -> Diagrams and disable "anti-aliasing."

mdailey, thanks a lot for your help!!! :)

---

