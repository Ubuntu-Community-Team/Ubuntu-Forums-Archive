---
title: "Can't install software"
date: 2007-06-14
forum: General Help
---

### Post by golfy on 2007-06-14
I an trying to install some software as per this link [http://ubuntuforums.org/showthread.php?t=472006](http://ubuntuforums.org/showthread.php?t=472006)

but it comes up with the lines below 

Setting up build-essential (11.3) ...
ubuntu@ubuntu:~/Desktop/liarliar-0.5.2$ ./configure
bash: ./configure: /bin/sh^M: bad interpreter: No such file or directory
ubuntu@ubuntu:~/Desktop/liarliar-0.5.2$ /configure
bash: /configure: No such file or directory
ubuntu@ubuntu:~/Desktop/liarliar-0.5.2$ configure
bash: configure: command not found
ubuntu@ubuntu:~/Desktop/liarliar-0.5.2$ 



Can anyone show me how to install it please.

Thanks,

Dave

---

### Post by hikaricore on 2007-06-14
I could be wrong here, but it looks like the files for whatever you're trying to install were saved in dos format at some point.

So instead of the configure file pointing to /bin/sh it's pointing at /bin/sh^M which is supposed to be a carriage return (new line).

You may want to try the command:

```
dos2unix configure
```

It will (attempt) to convert this/these files properly to a use-able format.

Then try running **./configure** again. :)

---

