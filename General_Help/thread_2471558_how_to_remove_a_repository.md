---
title: "how to remove a repository?"
date: 2022-02-02
forum: General Help
---

### Post by Skaperen on 2022-02-02
i added a PPA repository.  i used **[FONT=courier new]add-apt-repository ppa:foobar/foo[/FONT]**.  so, how do i remove it?
```

lt2a/forums /home/forums 81> del-apt-repository ppa:foobar/foo
bash: del-apt-repository: command not found
lt2a/forums /home/forums 82> rem-apt-repository ppa:foobar/foo
bash: rem-apt-repository: command not found
lt2a/forums /home/forums 83> rm-apt-repository ppa:foobar/foo
bash: rm-apt-repository: command not found
lt2a/forums /home/forums 84> sub-apt-repository ppa:foobar/foo
bash: sub-apt-repository: command not found
lt2a/forums /home/forums 85> 

```
i used "foobar/foo" as a substitute PPA name for this post.  i used the real one in the actual commands (done via **[FONT=courier new]sudo[/FONT]**)

---

### Post by deadflowr on 2022-02-02
Add -r or --remove to the original  add-apt command
If the orignal command was
```
sudo add-apt-repository ppa:foobar/foo  
```
put an -r in it like
```
sudo add-apt-repository **-r **ppa:foobar/foo  
```

---

### Post by Skaperen on 2022-02-03
thank you!

---

### Post by Skaperen on 2022-02-03
cmd/del-apt-repository:
```

#!/usr/bin/env python3
import os,sys
os.execv('/usr/bin/add-apt-repository',['-r']+sys.argv[1:])

```
note: not tested, yet.

---

