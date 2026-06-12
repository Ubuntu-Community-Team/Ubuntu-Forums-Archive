---
title: "Touchscreen disabled after Sleep/Hibernate need help running script on wake."
date: 2015-09-29
forum: General Help
---

### Post by Haki_Red on 2015-09-29
Hello guys I have a Lenovo X1 Carbon Gen 3, I just installed **Ubuntu-Gnome-15.0** on it and I have an issue where the touchscreen would disable on sleep but then it does not automatically re-enable on wake thraw | resume. 

I can do it manually by entering this on the terminal

/usr/bin/xinput set-prop "ELAN Touchscreen" "Device Enabled" 1

I've tried a few times to make a script on wakeup here's one example 
```

#!/bin/sh
#
# 99touchscreen: suspend/wakeup Touchscreen input device


case "$1" in
hibernate|suspend)
/usr/bin/xinput set-prop "ELAN Touchscreen" "Device Enabled" 0
;;
thaw|resume)
/usr/bin/xinput set-prop "ELAN Touchscreen" "Device Enabled" 1
;;
*) exit $NA
;;
esac



```

I'm not that familiar with shell and I'm not sure if indentation is part of the syntax I just copied this script.
I have chmod a+x on it as well

I placed the scripts on both 
/lib/systemd/system-sleep and [B]/etc/pm/sleep.d/ 

[/B]The other variant of the script is 
```

#!/bin/sh
case $1/$2 in
  pre/*)
    /usr/bin/xinput set-prop "ELAN Touchscreen" "Device Enabled" 0
    # Place your pre suspend commands here, or `exit 0` if no pre suspend action required
    ;;
  post/*)
    /usr/bin/xinput set-prop "ELAN Touchscreen" "Device Enabled" 1
    # Place your post suspend (resume) commands here, or `exit 0` if no post suspend action required
    ;;
esac



```

It happens when I close the lid, I believe the default action is sleep.
I just can't get the script to run, could my conditions be wrong? 

Thanks

---

