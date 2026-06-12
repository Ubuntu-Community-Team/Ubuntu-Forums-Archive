---
title: "HOW TO: determine whether the computer is powered by battery or line power"
date: 2008-04-21
forum: General Help
---

### Post by lviggiani on 2008-04-21
Hi,
is there any bash script/command to determine determine whether the computer is powered by battery or line power?
Thanks.

---

### Post by nicedude on 2008-04-21
If your using Ubuntu which will mean you have the Gnome desktop installed, then just hover mouse over an empty space on top or bottom toolbar and right click - in the shortcut menu choose "add to panel" then when window pops up scroll half way down till you see "System & Hardware" section & look for battery charge monitor and select it. you will then have a icon on the toolbar whenever your laptop is unplugged displaying the status of your battery. So when your plugged in it doesn't show up on toolbar but when you unplug it pops up with a messege and then stays displaying icon with status of batt.

---

### Post by lviggiani on 2008-04-21
Hi nicedude,
thanks for your answer but unfortunately this is not what I meant. :(

I need to check it within a script, like for example:

#!/bin/bash
if [ current_power_source_is_battery ]; then
     do_something
else
    do_something_else
fi

Thanks.

---

### Post by ryanhaigh on 2008-04-21
You may want to look at using the output of the acpi command. Looking at the man page for that application indicates that it will return infor about the current state of battery/ac power so it may be useful. There may also be entries under /proc/acpi/battery or ac_adaptor which you could parse. 

You may also want to look at the scripts for laptop-mode which must somehow determine the state of the battery. 

I also found this which looks like it could be useful.
[http://www.cs.bham.ac.uk/~axs/laptop/batt-crit.txt](http://www.cs.bham.ac.uk/~axs/laptop/batt-crit.txt)

---

### Post by lviggiani on 2008-04-21
Thank'you very much!
That's exactly what I was looking for!

Within the script you've linked to your reply I have found the command:

grep -o on /proc/acpi/ac_adapter/AC/state

which return "on" if you're in AC mode and nothing "" if you're in battery mode.

Thanks again!

---

