---
title: "Java in Firefox 2"
date: 2008-05-01
forum: General Help
---

### Post by Zalbor on 2008-05-01
I went back to using firefox 2, as 3 is still too buggy for me, and I noticed that the java plugin for it is not installed. I do have the packages sun-java6-bin, -jre and -plugin installed. If I go on a webpage that requires Java and ask firefox to install it, it says the package is alreay installed (which it is) but still doesn't load the plugin.
I guess I have to copy/link an .so file somewhere, but I don't know which one and where... Any help?

---

### Post by kevlar16 on 2008-05-01
The solution is here:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/211309](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/211309)

---

### Post by Zalbor on 2008-05-01
Thanks :) I found another way that works and I'm using it now actually. It was in this thread: [http://ubuntuforums.org/showthread.php?t=773987](http://ubuntuforums.org/showthread.php?t=773987)

Linking the .so files worked, I did the same for the vlc plugin. But your way might be a more "proper" one.

---

