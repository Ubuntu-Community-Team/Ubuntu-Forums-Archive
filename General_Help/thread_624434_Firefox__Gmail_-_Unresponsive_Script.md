---
title: "Firefox / Gmail - Unresponsive Script"
date: 2007-11-26
forum: General Help
---

### Post by JedV on 2007-11-26
Firefox (versions 2.0.0.8 and 2.0.0.10) has been encountering an "Unresponsive Script" when I am trying to open messages in Gmail.  See the attached screenshot.  Clicking continue results in Firefox hanging up,  and then needing a force quit.  This issue has popped up in the last 3 days.

[[IMG]http://img107.imageshack.us/img107/1200/screenshotwarningunrespcb2.th.png[/IMG]](http://img107.imageshack.us/my.php?image=screenshotwarningunrespcb2.png)

Does this look like a Firefox problem, an Ubuntu problem, or a Gmail problem?

Note:  My system is running Ubuntu Gutsy 7.10 64 bit.  This problem does not occur when I run Firefox32 1.5.0.6, or IE 6 (IEs4Linux).

---

### Post by superwad on 2007-11-26
I'd say if it occurs only in one particular version of Firefox, it might be the installation.  Have you tried removing Firefox 2 and reinstalling it?

---

### Post by JedV on 2007-11-27
I tried re-installing Firefox 2, and also tried the Firefox 3 alpha.  The issue is present in both versions.

---

### Post by JedV on 2007-11-27
I've narrowed the cause down to AdBlock Plus - must have been a recent update that broke something.  Nevertheless, this useful extension can be disabled for Gmail.

This discovery was made by running Firefox from the terminal in Safe Mode, and temporarily killing the ad-ons.  From there it was a process of elimination.

```
firefox -safe-mode
```

---

### Post by K.Mandla on 2007-11-27
There's also a Firefox setting that might help. Open about:config in your browser bar and look for this key ...

```
dom.max_script_run_time
```
If I remember right, increasing the value of that key gives the browser longer to process the script before warning you.

I need this one a lot for older machines, which can't run through the script in the time the key allows. :roll:

---

### Post by nthpro on 2007-11-28
Disable ad-block plus on the mail.google and it will fix itself.  Something recently broke it...

---

### Post by PerivaleElvis on 2007-11-28
I had the same problem this week and discovered it was Adblock Plus. I disabled Adblock plus in GMAIL to fix it. Changing script run times seems a drastic step to take.

---

### Post by dogeatery on 2008-03-02
This may sound like a dumb question: how do I block adblock plus in gmail?

---

### Post by abhiroopb on 2008-03-12
I enabled disabled adblock plus for the gmail site.

To do so look for the little ABP logo in the bottom right corner (on your statusbar) click on it and there will be a something that says disable for mail.googl.com, click on it.

Unfortunately I'm still getting the error, is there anything else I need to do?

---

### Post by dogeatery on 2008-03-12
I've asked a lot of dumb questions but that was the dumbest!  Thanks for the tip :)

---

