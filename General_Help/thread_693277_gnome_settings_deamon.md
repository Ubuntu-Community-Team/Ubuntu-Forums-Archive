---
title: "gnome settings deamon"
date: 2008-02-10
forum: General Help
---

### Post by wabbalee on 2008-02-10
hello all,

I have a problem with the gnome settings deamon in gutsy studio edition

i have read other threads and did what was suggested by strabes here: [http://ubuntuforums.org/showthread.php?t=293193](http://ubuntuforums.org/showthread.php?t=293193)

then i thought it fixed it but still there are problems;

i put the gnome-settings-deamon in '**system -> preferences ->sessions -> start up programs**' and it seemed to have fixed it; the ubuntu studio theme gets loaded as it should but when i start '**preferences -> appearance preferences**' i get the following message first:

[B]Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.[/B]

this is where i get lost and not sure what to do to check what is mentioned in the error message. there are some libbonobo files installed but i would assume that is quiet normal.

i know without this deamon running (properly) some desktop settings (and possibly more) cannot be changed.

any advice is greatly appreciated
ron

---

### Post by stooshbunutu on 2008-03-01
did you install ubuntu gutsy gibbon and theninstall the ubuntu studio packages

or

did you download and install from the ubuntu studio website?

If you did the first this just happens every time you boot up because something in the ubuntu studio package upsets the gnome-settings-daemon and so it has to be loaded manually every time you boot up (what you do by entering it into the sessions log) the message will come up everytime because it lets you know it din't load automatically like it should but will l:)oad from the sessions.

If yo did the second then i'm afraid I cant really help you

Hope this helps

---

### Post by wabbalee on 2008-06-07
sorry for not answering any sooner stooshbunutu, I did not know there was a reply. I must change the way ubuntuforums notifies me when a post or thread gets a reply so i can respond quicker.

this concerns my daughter's machine and she has not been complaining about it any more so i let it rest.

i have 2 of 4 of my machines upgraded to hardy since and working fine, with a small problem on my laptop being temporary unresponsive occasionally but that is for another thread

thanks for your reply anyway

ron

---

