---
title: "Scripting Program Installations"
date: 2007-12-12
forum: General Help
---

### Post by kackler on 2007-12-12
I have several programs that I install everytime I setup a server or desktop. I've never written a shell script and I'm not 100% sure if it needs to be located somewhere specific, I have it on the desktop and it's named update.sh. Here is my first test script:

#!/bin/sh
sudo apt-get update

Here is the command I use to try and run it:

~/Desktop$ ./update.sh 

But it says command not found.

---

### Post by jken146 on 2007-12-12
It should be ```
#!/bin/bash
``` at the top.

You also need to make the script executable.

The right way to run it is

```
./<script file>
```

---

