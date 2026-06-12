---
title: "Google Chrome - an update not working, hanging all updates."
date: 2014-01-30
forum: General Help
---

### Post by Wroger on 2014-01-30
This happened out of the blue.

Google Chrome (Chromium) installed as a fall back browser...

Decided to update - and oddly enough, in amongst it was a FORCED update of Google Chrome/chromium

I thought "MMMMM this is a bit suspect."

The Chrome update would not work.

Now the updater jams and will not update anything, the software centre starts up and closes, and the synaptic package manager won't start.

The updater and the synaptic give a more or less identical message:


E: The package google-chrome-stable needs to be reinstalled, but I can't find an archive for it. 
E: Internal error opening cache (1). Please report.


Google Chrome is in there and it runs fine.

And now after the updater didn't - aside from the terminal, none of the GUI software runs.

How to fix?

Ideas wanted.

Thanks in advance

---

### Post by cariboo on 2014-01-30
IF you have synaptic package manager installed, you can use it's broken filter to remove the misbehaving package, otherwise try:

```
sudo apt-get purge chrome
```

The run:

```
sudo apt-get update && sudo apt-get upgrade
```

---

