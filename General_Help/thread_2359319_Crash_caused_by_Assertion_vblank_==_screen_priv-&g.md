---
title: "Crash caused by Assertion vblank == screen_priv-&gt;flip_pending failed"
date: 2017-04-22
forum: General Help
---

### Post by dean.w.schulze on 2017-04-22
This happened regularly a week ago and I thought I had it solved by turning Dim Screen to Save Power off in Brightness and Lock settings.  It just happened again.  Since the error dialog doesn't allow copying I took a series of screen shots of the contents (attached).

The cause seems to be:  Assertion vblank == screen_priv->flip_pending failed.  Is there a place to file a bug over this?


[ATTACH=CONFIG]274706[/ATTACH][ATTACH=CONFIG]274707[/ATTACH][ATTACH=CONFIG]274708[/ATTACH][ATTACH=CONFIG]274709[/ATTACH][ATTACH=CONFIG]274710[/ATTACH]

---

### Post by deadflowr on 2017-04-22
>  Is there a place to file a bug over this?
That's the crash report which should have asked to report it, or at least already sent it in.
Crash reports are in /var/crash.
Usually clicking on the crash file will open the apport crash report program.
It should show an option to report it.

---

