---
title: "Kitchensync / Kontact"
date: 2008-01-09
forum: General Help
---

### Post by mafitzpatrick on 2008-01-09
Currently you have to close Kontact before syncing otherwise it hangs and (in my experience) starts creating duplicates the next time you update.  To stop myself doing this I've written the following script:

```

#!/bin/sh

if [ "`dcop | grep -i 'kontact'`" = "kontact" ]; then
	dcop knotify default notify eventname appname 'Kontact is open! Close before Syncing.' '' '' 2 0
else
	kitchensync
fi

```

Basically when you run it it checks to see if Kontact is open/running and if so pops up the error message. If there is no sign of Kontact it will run Kitchensync for you.  Create a file named kitchensync.sh and save it into your home directory. Then click to "Add Application to panel >> Add non-KDE Application" and put in ~/kitchensync.sh as the path. You can add the icon (search for Kitchen to find the correct icon from the list).

There you'll have a nice sync button on your panel which will make sure you don't sync while Kontact is open!

If there are any obvious improvements to the script let me know, first attempt at writing one :)

Thanks.

---

### Post by K.Mandla on 2008-01-09
Moved to General Help.

---

