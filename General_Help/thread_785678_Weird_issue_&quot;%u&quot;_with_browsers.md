---
title: "Weird issue &quot;%u&quot; with browsers"
date: 2008-05-07
forum: General Help
---

### Post by Bino on 2008-05-07
I did a fresh install of Hardy which seemed to work just fine. Earlier this week I had issues with Firefox3 where it was closed but still set as active in the process manager. Killing and restarting didn't work and when I wanted to restart my system by pressing the "restart" button my system didn't do anything anymore. So I had to close it down manually by pressing the power button.

After restarting I got an error at login which said something about my user account needed to have 644 privileges ( /HOME/.drmc not being writeable). I browsed around on the forums and the solution would be to chmod 700 my home/user dir. This worked, no error anymore at login.

But after having done this I noticed something weird with both my firefox and opera browser at startup. They now both start with page "%u" ([http://%u.com](http://%u.com) for firefox) although I have other homepages set.

Any idea what causes this and how to solve it?

---

### Post by lisati on 2009-04-08
I vaguely recall something similar to this coming up for me once while I had 7.04 installed on one of my laptops. As I recall, the solution included checking what options FF was called with from the menu, but the relevant link in the forums eludes me for the moment.

You might also want to check your FF home page settings. This can be found on Edit->Preferences menu within FF, and clicking on the "Main" tab.

Edit: I'm thinking of the "%u" thingummy...

---

