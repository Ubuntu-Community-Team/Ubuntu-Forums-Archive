---
title: "[SOLVED] Mozilla Firefox on mouse click question"
date: 2008-05-15
forum: General Help
---

### Post by shadowlab on 2008-05-15
Is there any setting in the about:config file of Firefox that will automatically select all the text in the address field on mouse-click, so when I start typing my new destination it will just blow the old one away?

I know this question may seem trivial, but it's a bit annoying having to do a ctrl-a each time before I start typing.

---

### Post by bmac on 2008-05-15
In the firefox ulr window type:
about:config

In the filter box type:
browser.urlbar.clickSelectsAll

 it will show up in the window then right click on the "browser.urlbar.clickSelectsAll" and select toggle.

Close the about:config window or tab.


Hope this helps...

---

### Post by shadowlab on 2008-05-16
Thank you bmac. Worked like a charm!

---

### Post by bmac on 2008-05-16
Really don't know why that isn't defaulted "Ture". I believe it defaults "True" in M$ when Firefox loads in that other OS...:smile:
I also think the configuration should be more easily accessible and with a GUI... Strange...

---

