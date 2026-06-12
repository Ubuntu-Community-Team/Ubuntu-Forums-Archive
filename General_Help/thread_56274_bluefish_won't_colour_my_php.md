---
title: "bluefish won't colour my php"
date: 2005-08-11
forum: General Help
---

### Post by fekimoki on 2005-08-11
why my bluefish won't colour my php loaded file into it?
its just plain black, and just a blue colour inside of " "

thx!
i install usign apt-get, and didn't touch any bluefish preferences.

---

### Post by drummer on 2005-08-12
[QUOTE=fekimoki]why my bluefish won't colour my php loaded file into it?
its just plain black, and just a blue colour inside of " "

thx!
i install usign apt-get, and didn't touch any bluefish preferences.[/QUOTE]
 Pressing F5 refreshes the syntax highlighting in the code vew. The file must be saved, with the extension php of course, before it does any highlighting. Also, check that the file starts with "<?php" and ends with "?>".. I had funny highlighting in my php if the php header wasn't at the very start (ie. if I had HTML at the top and blocks of PHP later on) even if the file was saved *.php

---

