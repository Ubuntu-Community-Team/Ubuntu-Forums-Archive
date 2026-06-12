---
title: "Problem with Firefox 1.0.4--and a solution"
date: 2005-05-29
forum: General Help
---

### Post by jonrkc on 2005-05-29
I downloaded and installed, using Synaptic, Firefox 1.0.4 from the backport repository.  It, and the version 1.0.2 that got installed as default with Ubuntu, had a strange non-standard "save file" dialog that was missing the option to save as "HTML only" or text.  It didn't even look like a Firefox dialog box.  I posted a screenshot at [www.jonrkc.com/my_images/Firefox_screen_shot.png](www.jonrkc.com/my_images/Firefox_screen_shot.png) in case you want to see what the dialog looks like.

I was worried that my machine might have been compromised despite fairly elaborate security precautions I take.  There has been a "save file" vulnerability recently in Firefox, adding to my concern.

At the suggestion of a Linux users' group member, I reinstalled Firefox.  Only this time I obtained the tar.gz package from Mozilla.org and installed from that (v. 1.0.4).  The normal dialog box is back, with all the options and format that I was familiar with.

I have no idea what would cause non-standard features in an app, but it doesn't seem like a desirable thing to me....  I wanted to point this instance out in case it might help somebody else puzzled by the appearance of foreign elements in Firefox.

---

### Post by NeoChaosX on 2005-05-29
Or you could just do **sudo apt-get remove mozilla-firefox-gnome-support**, which removes the package that makes all Firefox save dialogs like the default GNOME/GTK save dialogs, and not have to wreck the Firefox package install.  :razz:

---

### Post by jonrkc on 2005-05-29
[QUOTE=NeoChaosX]Or you could just do **sudo apt-get remove mozilla-firefox-gnome-support**, which removes the package that makes all Firefox save dialogs like the default GNOME/GTK save dialogs, and not have to wreck the Firefox package install.  :razz:[/QUOTE]
 Aha!  So that's what was going on.  Thanks for cluing me in--I had no idea, and was fairly worried, too.  I'd never even heard of mozilla-firefox-gnome-support.  

Well, the installation I made with the tar'd package is working fine (after I fixed the interplay between Thunderbird and Firefox, which got wiped out in the course of installing the backported package) so I'm going to go with it.

Thanks for the clarification.  It's something else for me to keep in mind when I'm puzzled by little quirks now and then.

---

### Post by jnoreiko on 2005-08-06
[QUOTE=NeoChaosX]Or you could just do **sudo apt-get remove mozilla-firefox-gnome-support**[/QUOTE]

but that requires ubuntu-desktop to be removed too.
I removed that in warty for some reason and upgrading to Hoary went wrong because of it (I think).

---

