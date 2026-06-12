---
title: "User sleep and resume scripts"
date: 2012-11-17
forum: General Help
---

### Post by jeff.sadowski on 2012-11-17
I created a simple script to allow users to have sleep and resume scripts for laptops and such

/usr/lib/pm-utils/sleep.d/00user_scripts
```

#!/bin/bash

homes=`ls -l /home| awk '{print $3 ":/home/" $8 }'|sort|uniq`

run_script()
{
lines=`echo -e "${homes}"|wc -l`
x=1
while [ $x -lt $lines ]; do
let x=$x+1
home=`echo -e "${homes}"|head -n $x|tail -n 1|cut -d: -f2`
user=`echo -e "${homes}"|head -n $x|tail -n 1|cut -d: -f1`
script=${home}/$1
if [ -x ${script} ];then
su ${user} -c ${script}
fi
done
unset home
unset user
unset script
}

on_sleep()
{
run_script .sleep
}

on_resume()
{
run_script .resume
}

case $1 in
    hibernate|suspend|sleep)
        on_sleep
        ;;
    thaw|resume)
        on_resume
        ;;
    *) exit $NA
        ;;
esac

```

then any user can create a .sleep script in their home directory to run commands when the laptop is put to sleep and a .resume script in their home directory to run commands when the laptop is wakened back up. I use this to do an sshfs mount and unmount.

---

