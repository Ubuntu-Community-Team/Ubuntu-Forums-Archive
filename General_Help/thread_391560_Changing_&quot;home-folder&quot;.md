---
title: "Changing &quot;home-folder&quot;"
date: 2007-03-23
forum: General Help
---

### Post by Reschat on 2007-03-23
I have a problem - and you don't get the backstory this time - just the problem:

I can't get into Gnome because it loads the home-folder as "/home/karni/" when it in fact should be "/home/halfdan/".
I changed this in: "System" > "Administation" > "Users settings" > "Account 'halfdan' Properties" > "Advanced" > "Home directory"

But how to I change it "back" (to "/home/halfdan/" instead of "/home/karni/") in terminal/commandprompt? 

(And - no - Failsafe GNOME dosn't work)

---

### Post by AndrewBarber on 2007-03-23
Ok from a terminal, log in as your user then do
```
sudo nano -w /etc/passwd
```
Find (ctrl+w) your username and you should have a line like;
```

halfdan:x:1000:1000:*name*,,,:/home/karni:/bin/bash

```
Change the /home/karni to your new dir halfdan
So it should look something like;
```

halfdan:x:1000:1000:*name*,,,:/home/halfdan:/bin/bash

```
Exit nano(ctrl+x) and reboot.

---

### Post by Reschat on 2007-03-23
Thanks alot AndrewBarber. :) 
It worked perfect.

---

