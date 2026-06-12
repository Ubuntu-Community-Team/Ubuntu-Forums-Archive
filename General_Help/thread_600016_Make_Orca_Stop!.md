---
title: "Make Orca Stop!"
date: 2007-11-01
forum: General Help
---

### Post by Jamie Jackson on 2007-11-01
I wanted to try orca, so I went to System > Preferences > Universal Access > Assistive Technology Preferences and checked "enable assistive technologies."

I quickly got tired of that, and unchecked the box, but it won't stop starting up in new sessions. It presents me with a terminal screen with a voice selection prompt, and jabbers at me until I close the window.

How do I make it stop?

Thanks,
Jamie

---

### Post by moon2js on 2007-11-11
Trying go back to Accessibility Tech Prefs, click the Preferred Apps button, change to the Accessibility tab and make sure "Run at start" is unchecked.

---

### Post by kd7swh on 2007-11-11
you could always:

```
sudo killall orca
```

---

### Post by Jamie Jackson on 2007-11-12
> **moon2js said:**
> Trying go back to Accessibility Tech Prefs, click the Preferred Apps button, change to the Accessibility tab and make sure "Run at start" is unchecked.

That's it, thanks!

---

