---
title: "Need Help With Mass File Renaming"
date: 2006-10-30
forum: General Help
---

### Post by Keymaster on 2006-10-30
How do I rename about 176 files from *.mp3.ogg to *.ogg  Thanks

---

### Post by tatimmer on 2006-10-30
from the commandline I think this should do it:
mv *.mp3.ogg *.ogg

You might want to "mkdir" and "cp" a couple files into it and practice first.

for more info:
man mv
man mkdir
man cp

---

### Post by beerorkid on 2006-10-30
mvb works really good as well.  Simple and easy

[http://ubuntuguide.org/wiki/Dapper#How_to_rename_all_files_in_directory_at_once](http://ubuntuguide.org/wiki/Dapper#How_to_rename_all_files_in_directory_at_once)

---

### Post by aysiu on 2006-10-30
If you prefer a GUI, try KRename. It's in the repositories.

---

### Post by roberTO on 2006-10-30
Hi!

apt-get install thunar-media-tags-plugin

Great apps!

---

### Post by Breepee on 2006-10-30
thunar-media-tags-plugin looks very nice. Does it work with FLAC tags?

---

### Post by volanin on 2006-10-30
Just use rename.
It uses regexps, so it is very powerful and easy.
To rename every *.mp3 to *.ogg in the current dir, type:

rename 's#\.mp3\.ogg#\.ogg#' *

(The dots have to be prefixed with a backslash)
And there you go!
Enjoy.

---

### Post by jordilin on 2006-10-30
and here a little python script:
```
#!/usr/bin/python

import glob
import os

files=glob.glob("*.mp3.ogg")
for i in files:
	new_name=i[:-8]+".ogg"
	os.rename(i,new_name)
```

---

### Post by jordilin on 2006-10-30
> **tatimmer said:**
> from the commandline I think this should do it:
mv *.mp3.ogg *.ogg

You might want to "mkdir" and "cp" a couple files into it and practice first.

for more info:
man mv
man mkdir
man cp

That's wrong, and mv will complain!!

---

### Post by IcemanV9 on 2006-10-31
I agreed with volanin's recommendation. Just simply use **[COLOR="Orange"]rename[/COLOR]**.

Another method (works for me) ...
```
**[COLOR="Orange"]rename[/COLOR]** 's/\.mp3/\.ogg/' *.mp3
```

---

