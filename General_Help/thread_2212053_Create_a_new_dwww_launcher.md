---
title: "Create a new dwww launcher"
date: 2014-03-19
forum: General Help
---

### Post by cogset on 2014-03-19
I've been  trying to add a new launcher for the dwww application,as it relies on apache2 and I have this stopped in normal use,I've just written a simple one line script that starts apache2 and then launches dwww,and it  works fine in a terminal.
It doesn't however when I  try to launch that script from a custom application launcher,not even prepending the script path with sudo:it does work if I use  gksudo,but then it will open the Firefox profile for root,which is clearly not what I'm after.
What am I doing wrong?

---

### Post by ajgreeny on 2014-03-19
Show us the script contents, otherwise we are stabbing in the dark trying to suggest a reason.

---

### Post by cogset on 2014-03-19
Fair enough,it's really just a one  line command (well,actually three)

```
#!/bin/bash

#start apache server and then dwww

sudo /etc/init.d/apache2 start  &&  dwww
```

and as I've said it works in a terminal,but if I paste the location of this script in the Command field of the new custom launcher,nothing happens.

---

