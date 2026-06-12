---
title: "[SOLVED] Openoffice netbean integration"
date: 2007-11-19
forum: General Help
---

### Post by veloce on 2007-11-19
Is anyone out there using netbeans for openoffice development?  I cannot get it to run and can't find anyone using these two together!

The error I get when trying to create a new project is:


```

While executing an SDK Command, the following error happened:
/usr/lib/openoffice/sdk/linux/bin/uno-skeletonmaker: 4: basename: not found
/usr/lib/openoffice/sdk/linux/bin/skeletonmaker: 4: /usr/lib/openoffice/sdk/liniux/bin/.bin: not found


```

---

### Post by veloce on 2007-11-27
There is an error in the netbeans openoffice integration at least under Ubuntu.  The problem lies in these wrapper scripts, located in /usr/lib/openoffice/sdk/linux/bin.  There are 14 identical scripts, one for every .bin file in the directory.  Each is used to call the .bin file with the same name.

They look like this:

```
#!/bin/sh
# wrapper script for OOos SDK programs

LD_LIBRARY_PATH=/usr/lib/openoffice/program /usr/lib/openoffice/sdk/linux/bin/`basename $0`.bin "$@"
```

The problem is that Netbeans doesn't provide a complete PATH variable so the program "basename" that returns the name of the file fails. 

To fix this, I changed the file to this:

```
#!/bin/sh
# wrapper script for OOos SDK programs

LD_LIBRARY_PATH=/usr/lib/openoffice/program /usr/lib/openoffice/sdk/linux/bin/`/usr/bin/basename $0`.bin "$@"

```

Each of the 14 shell script files in the directory need to be changed (though I'd only got as far as using "uno-skeletonmaker".)

I've reported the bug and the work around to the openoffice sdk development team.

---

