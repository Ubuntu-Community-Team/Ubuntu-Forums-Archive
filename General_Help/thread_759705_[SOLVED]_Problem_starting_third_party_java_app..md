---
title: "[SOLVED] Problem starting third party java app."
date: 2008-04-19
forum: General Help
---

### Post by doug1212 on 2008-04-19
Hello Ubuntuists,
I have downloaded a third party java application that is started with a script "start.sh" this appears to call a .jar file with its parameters.
Now if I cd to the directory and do ./start.sh the app starts up and functions fine but I am trying to add it to the applications menu with no joy, if I give the full path to start.sh it fails to start and complains about not finding files:confused:.
I am obviously missing somthing, any ideas?
Thanks, Doug.

---

### Post by ibuclaw on 2008-04-19
How big is the start.sh script?

If it's relatively small, can you post it up on the forum for reading.

Thanks.

But in the mean time, try this as an attempt.

A) Create a text file, save it as the appname, or **appname**.sh. And copy this into it.
Change it to match your system.
```

#!/bin/bash

# Path to directory, is the path where the start.sh script is.
cd **/PATH/TO/DIRECTORY**
exec ./start.sh

```


Mark it executable and copy it to your /usr/local/bin directory.
```
 sudo cp **appname**.sh /usr/local/bin/**appname**.sh
```

And in the Applications Menu, create a shortcut with the command to run as "appname.sh", without quotation marks..

Regards
Iain

---

### Post by doug1212 on 2008-04-19
Many thanks tinivole,
Your instructions did indeed get my app menu shortcut working.
Still lots to learn :), Doug.

---

