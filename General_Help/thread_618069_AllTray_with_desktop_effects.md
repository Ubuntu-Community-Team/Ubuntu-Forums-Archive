---
title: "AllTray with desktop effects"
date: 2007-11-20
forum: General Help
---

### Post by Angelbeast on 2007-11-20
Does anyone know how to get AllTray to work with the desktop effects enabled?

---

### Post by emid on 2007-11-20
> **Angelbeast said:**
> Does anyone know how to get AllTray to work with the desktop effects enabled?

If I remember correctly you could use Alt-F2 and type "alltray" + the name of the app, or you could do the same thing from the deskbar.

---

### Post by Angelbeast on 2007-11-20
> **emid said:**
> If I remember correctly you could use Alt-F2 and type "alltray" + the name of the app, or you could do the same thing from the deskbar.

That worked thank you...Now this may be a dumb quetion but is there any way to make a script for that or something that i can just clck on in the deskbar?

---

### Post by emid on 2007-11-20
I think if you made a script like this:
```

#!/bin/bash

alltray (name of application)
exit


```

and saved it as alltray.sh or something it would work.  I think you would have to then make it executable.

```

chmod +x (name of script)

```

That's my guess.

---

