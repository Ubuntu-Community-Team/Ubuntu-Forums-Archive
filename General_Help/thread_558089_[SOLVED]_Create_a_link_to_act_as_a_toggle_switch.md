---
title: "[SOLVED] Create a link to act as a toggle switch"
date: 2007-09-23
forum: General Help
---

### Post by amadeus266 on 2007-09-23
I have 2 links on my panel, one to start to start compiz and one to stop it. Is it possible to have a single link that will start a program if it isn't running, or stop it if it is?

---

### Post by Keyper7 on 2007-09-23
I think a script that checks and sets an environment variable could do the trick.

---

### Post by amadeus266 on 2007-09-23
I'm not a programmer. Can anyone tell me how do this?

---

### Post by amadeus266 on 2007-09-25
I'm sure SOMEONE out there knows how to do this. I'm also sure that I'm not the only one who would use such a script.:guitar:

---

### Post by Adramelech on 2007-09-26
Im not even decent at bash scripting and i dont have compiz installed, please change the values to yours, put this text into a file and give it executable permission:

#!/bin/bash
if [ -n "$(pidof compiz_process_name)" ]
then
   command_to_shut_down_compiz
else
   command_to_start_compiz
fi

---

### Post by aidanr on 2007-09-26
```
#!/bin/bash
if ps ax | grep -v grep | grep compiz.real > /dev/null
then
killall compiz.real && xfwm4
else
compiz-manager
fi
```

Of course this is for xfce, but gnome would be similar. Just replace xfwm4 with metacity and compiz-manager with whatever command you use to start compiz

---

### Post by amadeus266 on 2007-09-26
Thanks guys, I will give it a try.

aidanr, your posts worked to turn compiz off but doesn't turn it back on. I changed "compiz-manager" to "compiz --replace" and now it works. Thanks for pointing me in the right direction.

Will a moderator please mark this thread as solved. Thankyou.

---

