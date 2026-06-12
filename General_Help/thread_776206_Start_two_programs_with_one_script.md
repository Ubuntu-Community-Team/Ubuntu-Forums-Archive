---
title: "Start two programs with one script?"
date: 2008-04-30
forum: General Help
---

### Post by WiFi Ed on 2008-04-30
Can I use one .sh script to start two programs? I currently use the delayed startup script from the Conky how-to thread to start Conky 15 seconds after logging in (.conky_start.sh).

I want to delay the start of Avant Window Manager in a similar fashion and it would be convenient to add AWN to the same script. That way, I would only have the one script called from the Sessions thinga-ma-jig.

Thanks in advance,

Ed

---

### Post by Monicker on 2008-04-30
You can put multiple commands in a script. 
```


#!/bin/bash

command1 &

sleep 5 

command2
```


Normally the script would not start command2 until command1 has finished, which is why I used the & to background the first command.

There may be a better way to do this.  I'm more comfortable with perl than bash scripting.  :P

---

### Post by WiFi Ed on 2008-04-30
Thanks for the response. Unfortunately, I couldn't get both conky and awn to start from the same script (most likely because I'm an idiot:-)), but I was able to do it using two separate scripts. The end result was what I wanted, that is, Ubuntu to load and settle down, then start Conky, then start AWN after that.

I do appreciate your willingness to help me though! Thanks again,

Ed

---

### Post by newb1e on 2008-04-30
Post your script here, maybe we can help:popcorn:

---

### Post by ryanhaigh on 2008-04-30
This is my startup script
```

#!/bin/bash
sleep 5 &&
yakuake &
pidgin &
thunderbird &
glipper &
deluge &
firefox &
#kdocker qtwengophone &
gnome-do &
brightside &
exit 0

```

&& means continue if and only if the preceeding command returns 0, this means the command has to complete so a return code is..well returned and that this return code must be 0 indicating no errors.

---

### Post by WiFi Ed on 2008-05-01
> **newb1e said:**
> Post your script here, maybe we can help:popcorn:

Ok! Here's the conky startup script I'm using:[PHP]#!/bin/bash
sleep 20 && conky;[/PHP]

and for AWN:[PHP]#!/bin/bash
sleep 25 && avant-window-navigator;[/PHP]

I tried combining them as:
[PHP]#!/bin/bash
sleep 20 && conky;
sleep 25 && avant-window-navigator;[/PHP]

That results in conky starting, but not AWN.

---

### Post by duggum on 2008-05-01
WiFi Ed,

Change your combined code to this:

```
#!/bin/bash
sleep 20 && conky &
sleep 25 && avant-window-navigator &
```

The reason yours doesn't get beyond conky is because the script is waiting for conky to exit before moving on to AWN. As mentioned in a previous post, you can't move on to another command until the previous command exits unless you run the previous command in the background. That is what the single ampersand (&) does. It dumps the process to the background and allows the script to move on to the next line.

To confirm this you should be able to run your original script, then enter "killall conky" in a terminal window. AWN should then start because conky has exited.

Hope this helps.

duggum

---

### Post by ryanhaigh on 2008-05-01
```
#!/bin/bash
sleep 20 && conky &
sleep 5 && avant-window-navigator &

```
unless you want to wait 45 seconds

---

### Post by WiFi Ed on 2008-05-01
Thanks duggum and ryanhaigh! That works exactly as I wanted. I'll adjust the sleep time downward a bit now that the startup sequence is fixed...

Thanks again and I'll google up a bash tutorial or two so I won't be so helpless in the future :-)

---

