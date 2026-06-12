---
title: "Nautilus python script not working"
date: 2007-01-10
forum: General Help
---

### Post by maruchan on 2007-01-10
Can anybody help me  troubleshoot this? I think there might be a problem with my Python setup but I don't know how to diagnose it.

Here is the script that does nothing when I click on it:

```
#!/usr/bin/env python

import os
import urllib
import urlparse

uris = os.environ['NAUTILUS_SCRIPT_SELECTED_URIS'].split('\n')[:-1]

for uri in uris:
unquoted_uri = urllib.unquote(uri)
path = urlparse.urlsplit(unquoted_uri)[2]
dirname = os.path.dirname(path)
command = 'file-roller -e "%s" "%s"' % (dirname, path)
os.system(command)
```

My other non-python scripts work fine.

---

