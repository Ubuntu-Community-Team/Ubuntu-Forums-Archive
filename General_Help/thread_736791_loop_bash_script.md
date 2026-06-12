---
title: "loop bash script"
date: 2008-03-27
forum: General Help
---

### Post by phillips321 on 2008-03-27
hi guys,

i have a simple script that checks for a network connection and then starts amsn and skype if it finds one:
```

#!/bin/sh
sleep 60
if eval "ping -c 1 www.google.co.uk"; then
 echo "Network located, starting amsn and skype"
 /home/user/Scripts/skype &
 amsn &
else
 echo "No network found, not starting amsn or skype"
fi
```
This code waits 60 seconds to give the interfaces time to acquire an ip etc...

I would like to edit this code so that instead it checks for a network connection every 10seconds and then executes the programs.

anyone know how to do this? would this work?
```

#!/bin/sh
10
sleep 10
if eval "ping -c 1 www.google.co.uk"; then
     echo "Network located, starting amsn and skype"
     /home/user/Scripts/skype &
     amsn &
     goto 20
else
     echo "No network found, not starting amsn or skype"
     goto 10
fi
20
```

---

### Post by ghostdog74 on 2008-03-27
use a loop
```

while true
do

    if eval "ping -c 1 www.google.co.uk"; then
        echo "Network located, starting amsn and skype"
        /home/user/Scripts/skype &
        amsn &
        break
    else
        echo "No network found, not starting amsn or skype"
     sleep 10
    fi

done 

```
or you can just put your script as cron job to execute every 10 sec. (without sleep)

---

### Post by phillips321 on 2008-03-27
thanks for this, it works fine.

I don't understand the while true part of the loop, while what is true?

any chance you can explain?

many thanks

---

### Post by lloyd_b on 2008-03-27
> **phillips321 said:**
> thanks for this, it works fine.

I don't understand the while true part of the loop, while what is true?

any chance you can explain?

many thanks

A "while" loop normally contains a condition that must be true in order for the loop to continue to execute.  Once the condition is no longer true, the loop exits.

The "while true" is simply a trick to create a loop that never exits - the "true" will always evaluate to true.

For a better understanding of what's going on, "man true" in a terminal window.  In this instance, it's using the bash built-in instead of the external program "true", but the results are the same.

Lloyd B.

---

