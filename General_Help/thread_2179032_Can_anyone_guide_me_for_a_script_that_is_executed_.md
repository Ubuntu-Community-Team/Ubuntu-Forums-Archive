---
title: "Can anyone guide me for a script that is executed when plugged off ac."
date: 2013-10-06
forum: General Help
---

### Post by 83W7HLn on 2013-10-06
Hi, im not totally new to the world of Linux but i have still much to learn, my question here is i need a script that is executed when i plug off the power cable or when starting on battery.

Anyone know where to put this?

The thing is i have two Graphics cards in my PC one chip and an ATI card for games etc.....

So, from what i recognized when im just browsing and doing other (non graphically heavy) stuff (on battery) the IDG is activated but the ATi- card is still using power in the background, and i do not use it.

My problem is that the battery is gone after about one hour from just doing cpu-light stuff and thats not good.

Im pretty sure it has to do with the ATi-card and from that point i think it would be best to shutdown the ati-card when on battery.

But im confused as i dont know where to put it that it gets executed when on battery and i dont know how to write a script.

I have the proper terms ready for vgaswitcheroo.

Any help would be greatly appreciated, maybe there exists a script that i only have to modify and to put the right command in or so?

Excuse me for mistakes but im not a native english speaker.

---

### Post by Toz on 2013-10-06
Hello and welcome to the forums. 

When your laptop changes power status (a/c vs battery), scripts in /usr/lib/pm-utils/power.d and /etc/pm/power.d are run. User-created scripts should be added to the /etc/pm/power.d directory as this location won't get over-written during pm-utils updates. The format of the file should be like:
```

#!/bin/bash
case $1 in
    true) #battery mode
           # "on-battery" commands here
    ;;
    false) #a/c mode
            # "on-a/c" commands here
    ;;
esac
exit 0
```
...make sure the file is executable.

You can review the log file /var/log/pm-powersave.log to see the status of the script as it runs between power changes.

---

