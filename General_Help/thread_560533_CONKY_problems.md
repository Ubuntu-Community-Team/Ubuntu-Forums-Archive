---
title: "CONKY problems"
date: 2007-09-26
forum: General Help
---

### Post by Nick w on 2007-09-26
Hi Team..

Followed the Conky install to a TEE.. The issue i have is when i start up the laptop from a shut down Conky doesnt load.  Well it does but once it finished booting up Conky disappears.. i have added Conky to the Sessions
I also read and then tried the -d switch after the command "conky" in the session options

Its like i can see the orange background load. then conky kicks in then once my background comes in and then conky disappears 

Any ideas..

Thanks
Nick

---

### Post by FuturePilot on 2007-09-26
I had that same problem. You need to make a script to start Conky after so many seconds. So do this
```
gksudo gedit /usr/local/bin/start_conky.sh
```
Copy and paste this into the file
```
#!/bin/bash
sleep 15;
exec conky -d
```
Save then do this to make it executable
```
sudo chmod +x /usr/local/bin/start_conky.sh
```
Then add ```
start_conky.sh
```
to the Sessions menu.

You can change the delay for when Conky starts by changing the number after sleep. That is the delay time in seconds.

---

### Post by Nero_Flint on 2007-10-28
Thanks for this help FuturePilot...tried a couple of other workarounds but they didn't work and yours did. Conky now works like a charm. :)

---

