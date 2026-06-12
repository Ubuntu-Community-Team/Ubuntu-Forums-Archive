---
title: "can some one make a bash script for me?"
date: 2008-02-02
forum: General Help
---

### Post by onesojourner on 2008-02-02
I tried to just create a launcher and run it as an application in terminal but it didn't work. So I guess it needs to be a bash script.

```
cd ~/xwii && ./xwii profiles/classic.xwii
```

---

### Post by Ocxic on 2008-02-02
copy this into as text file, and make it executable.

```

#!/bin/bash
cd ~/xwii
./xwii profiles/classic.xwii

```

---

