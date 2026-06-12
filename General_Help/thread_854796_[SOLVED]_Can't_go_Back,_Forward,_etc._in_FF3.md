---
title: "[SOLVED] Can't go Back, Forward, etc. in FF3"
date: 2008-07-09
forum: General Help
---

### Post by wenuswilson on 2008-07-09
I am extremely confused... I cannpt reload the page, stop, go back or forward on both the Edit options and the nav bar.

I have no idea why this is happening.
I've uninstalled and reinstalled in Synaptic. Same problem.

Any suggestions??

---

### Post by pytheas22 on 2008-07-09
Did you try moving the Firefox folder:
```

mv ~/.mozilla ~/.mozilla-OLD
```

That might help.  If not, a purge of Firefox may (just uninstalling and reinstalling through Synaptic doesn't get rid of all of Firefox, unless you choose the ~"remove completely including configuration files" option):
```

sudo apt-get remove --purge firefox
```

---

### Post by Kralizec on 2008-07-09
Do you mean you cannot at all, including using keyboard shortcuts (alt+left for back, alt+right for forward, f5 for refresh), or do you mean the buttons for the actions aren't visible?

---

### Post by wenuswilson on 2008-07-09
> **Kralizec said:**
> Do you mean you cannot at all, including using keyboard shortcuts (alt+left for back, alt+right for forward, f5 for refresh), or do you mean the buttons for the actions aren't visible?

Nope they don't work.

---

### Post by wenuswilson on 2008-07-09
Got it -- this is how...

In terminal--
> sudo apt-get remove --purge firefox
It says there are random lib files to be removed--
> sudo apt-get autoremove
Then reinstall--
> sudo apt-get install firefox

That did the trick.

[SOLVED]

---

