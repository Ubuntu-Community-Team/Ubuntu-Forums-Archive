---
title: "Can't turn off touchpad."
date: 2017-11-05
forum: General Help
---

### Post by Hewjr100 on 2017-11-05
I upgraded fro 17.04 to 17.10.  In 17.04 I had touchpad turned of.  After upgrade touchpad is on again, and there is no touchpad listed in devices.  The only options are general and mouse.  Is there another way to turn touchpad off?

Henry

---

### Post by #&amp;thj^% on 2017-11-05
Dose this work for you?
```
synclient TouchpadOff=1
```

---

### Post by Hewjr100 on 2017-11-05
Done and done, thank you.

Henry

---

### Post by #&amp;thj^% on 2017-11-05
Welcome.
To turn it back on:

```
synclient TouchpadOff=0
```
Just for the Record! ;)

---

### Post by Hewjr100 on 2017-11-09
Thanks, but one thing, can it be set to stay of when rebooting.

Henry

---

### Post by #&amp;thj^% on 2017-11-09
When using synclient a script will need to be used.
How about:
Save and name what you want.
```

if synclient -l | egrep "TouchpadOff.*= *0" ; then 
    synclient TouchpadOff=1 ; 
else 
    synclient TouchpadOff=0 ; 
fi
```

Or create an alias in your .bashrc Like:
```
alias tp="synclient TouchpadOff=1"
```
So to use the above I called it "tp"

---

### Post by Hewjr100 on 2017-11-09
Good to go.  Second option was easier for me.  Again thanks for all your help.

Henry

---

### Post by #&amp;thj^% on 2017-11-09
Your Very Welcome.
Cheers

---

