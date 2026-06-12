---
title: "Custom App Launcher - Kile 2.0 Problem"
date: 2008-02-01
forum: General Help
---

### Post by madcow72 on 2008-02-01
Hopefully a simple question, that I just don't know how to get around.  I recently installed Kile 2.0 after compiling from source 'cause it's not in the repositories yet.  To launch the application, [Sourceforge's website]("http://kile.sourceforge.net/help.php#compile") says to issue the command:  ```
KDEDIRS=$HOME/kile-bin:$KDEDIRS $HOME/kile-bin/bin/kile
```

That works just fine in a terminal to open Kile, but an icon on the menu bar would be way easier.  Unfortunately, creating a custom app launcher and using the above command gives me the following pop-up error:  ```
Failed to execute child process "KDEDIRS=$HOME/kile-bin:$KDEDIRS" (No such file or directory)
```.

Any ideas how to get around that?

---

