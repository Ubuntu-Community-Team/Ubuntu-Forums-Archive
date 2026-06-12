---
title: "System Settings Application Window Malfunction"
date: 2014-12-24
forum: General Help
---

### Post by dimethyl on 2014-12-24
When I open the "System Settings" Application a window opens displaying only the top black bar with the title of the application at the top left, a button/link for "All Settings" below the title, and a search bar to the right.  There is a short white bar below it, but I cannot reach any of the settings from the window.  I tried using the search bar and the "All Settings" button but neither led anywhere.  What can I do to restore the system preferences application to normalcy?

here is what i see when I open the system preferences application:
[IMG]http://s14.postimg.org/fpz1ts241/sysprefproblem.png[/IMG]

I am running Ubuntu 14.04 on a system 76 gazelle professional laptop

Thanks in advance

---

### Post by deadflowr on 2014-12-24
What happens if you run a search in Ubuntu's dash for one of the usually entries listed in the system settings.
Try a search for Appearance.
Does anything show up?
And if something does show up, if you try to open it does it actually open?

---

### Post by dimethyl on 2014-12-24
Appearances did show up, and when i clicked it it did open and gave me a normal window in system preferences.  When I click the "All Settings" button it leads to a normal system settings window too.  I closed the window and reopened the system settings, which now opens a normal window as it should.  Thanks deadflowr, problem appears to be solved, but I still don't know why or how i could diagnose why this happened.

---

### Post by deadflowr on 2014-12-24
Well I believe the package-name associated with it is called unity-control-center, fwiw.
(Which itself is a fork of the gnome-control-center)

So, if it happens again you could try launching it through the terminal, using that name.
(Which is actually pretty convenient; command to run it and package name being the same)
Sometimes the output from the terminal can be quite useful, though not all the time.

---

