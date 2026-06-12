---
title: "moved a file out of encrypted folder, fusermount -u wiped all files"
date: 2013-12-19
forum: General Help
---

### Post by sam_baker2 on 2013-12-19
I created an encrypted folder using encfs, and after opening the folder,
I opened a file within it using gedit, then moved that file to another folder on the system, 
( not to a folder within the encrypted folder itself, but to another folder outside of the 
encrypted folder )

mount the folder :
```

#!/bin/bash
encfs  -i3   ~/try/.test1  ~/try/test1
exit

```

I opened a file within test1 with gedit, then moved it to someplace else.

When I unmounted the folder: 
```

#!/bin/bash
fusermount -u ~/try/test1
rm -r ~/try/test1
exit

```

all of the encrypted files in .test1 were gone.

What gives?

---

### Post by sam_baker2 on 2013-12-19
I think I should edit my post a bit.
Actually, I didn't move the file to another folder. I simply
just moved it to another workspace, and then, when
I ran fusermount -u, all the files in the encrypted folder vanished.

---

