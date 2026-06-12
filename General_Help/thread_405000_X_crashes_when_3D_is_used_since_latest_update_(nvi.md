---
title: "X crashes when 3D is used since latest update (nvidia)"
date: 2007-04-09
forum: General Help
---

### Post by rocktorrentz on 2007-04-09
I did an apt-get update and apt-get upgrade yesterday and although i've completely forgotten what was updated I'm assuming it included a kernel or nvidia update. Anyway, when I booted up my PC this morning although X loads fine it crashes if I try to load beryl or glxgears. Has anyone else got this problem or am I the only one because I miss my wobbly windows?

---

### Post by teaker1s on 2007-04-09
worth looking to see if your xorg conf got updated, I had beryl crash after updating and it turned out to be my xorg.
strange part was beryl didn't complain about it when launching in terminal.

reverted to previous xorg config and it sorted it.

you don't say what drivers you use,the nvidia beta ones need re running every kernel update and watch for xorg changes

---

### Post by airxart on 2007-04-09
See if this helps.

[http://ubuntuforums.org/showthread.php?t=403164](http://ubuntuforums.org/showthread.php?t=403164)

:)

---

### Post by rocktorrentz on 2007-04-09
> **airxart said:**
> See if this helps.

[http://ubuntuforums.org/showthread.php?t=403164](http://ubuntuforums.org/showthread.php?t=403164)

:)

Thanks that fixed it :D But I appear to be using the 9746 driver rather than the 9755 driver like you.

---

