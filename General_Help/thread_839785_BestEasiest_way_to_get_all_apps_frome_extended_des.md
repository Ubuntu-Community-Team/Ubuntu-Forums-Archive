---
title: "Best/Easiest way to get all apps frome extended desktop on main display?"
date: 2008-06-24
forum: General Help
---

### Post by rickcr on 2008-06-24
I finally managed to get a laptop that uses a docking station working fine with an additional monitor so that I have an extended desktop. If I suspend the laptop and disconnect from the docking station the laptop thinks there are apps on the extended monitor. What's the easiest way to get those apps 'moved' back to the laptop display? I can't just drag them since I can no longer see that desktop. I'm sure there is an easy way to do this, but I'm stumped at the moment.

---

### Post by ryanhaigh on 2008-06-27
```

#!/usr/bin/python

#script to move all windows to the top left corner of the display
#using wmctrl

import os
import sys

command1 = 'wmctrl -r '
windows = []
command2 = '-e 1,0,0,-1,-1'

#the output of wmctrl -l has the hostname in it between
#the random stuff at the start and the window titles, get
#the hostname of the computer
host = os.popen('hostname').readline().strip() + ' '

#for all windows in the output of wmctrl -l -x
for window in os.popen('wmctrl -l -x').readlines():
    #append to list of windows
    windows.append(window.split(host)[1].strip())


#move all windows in the list using wmctrl
for window in windows:
fullCommand = command1+' "'+window+'" '+command2
    #print fullCommand
    os.system(fullCommand)

sys.exit(0)


```

Save this in a text file and name it something like moveall.py. Make sure the file is exectuable then you can either put it on the desktop or create a launcher to open it. 

I haven't been able to test that this actually moves the window as I only have an ssh connection to my ubuntu machine but the commands that the script produces seem to be correct.

---

### Post by rickcr on 2008-06-30
sorry for the late reply ryanhaigh...

thanks for the script. After fixing the one indent at line 25 and installing wmctrl it 'almost' seems to work. Unfortunately it moves all the windows to the external monitor instead of the other way around (where I want the external monitor windows moved to the laptop window). Also, it moved the gnome top panel as well, and got rid of the task bar panel, so not sure what went wrong there.

Any advice how can tweak the script a bit? It seems like it's almost there.

Thanks again.

---

### Post by ryanhaigh on 2008-07-01
```

#!/usr/bin/python

#script to move all windows to the top left corner of the display
#using wmctrl

import os
import sys

#place items you don't want moved in this list
blacklist = ['applet','Panel','panel','avant','awn']

command1 = 'wmctrl -r '
windows = []
command2 = '-e 1,**1285**,0,-1,-1'

#the output of wmctrl -l has the hostname in it between
#the random stuff at the start and the window titles, get
#the hostname of the computer
host = os.popen('hostname').readline().strip() + ' '

#for all windows in the output of wmctrl -l -x
for window in os.popen('wmctrl -l -x').readlines():
    #check if it is in the blacklist
    for item in blacklist:
        if str(window).find(item) >= 0:
            print 'Window: '+window+' contains '+item+' in blacklist'
            window = ''
    #append to list of windows
    if window:
        windows.append(window.split(host)[1].strip())

print windows

#move all windows in the list using wmctrl
for window in windows:
    fullCommand = command1+' "'+window+'" '+command2
    #print fullCommand
    os.system(fullCommand)

sys.exit(0)

```

Adjusted to exclude certain windows, I don't currently have dual monitors set up and its likely you use a different configuration but changing the position of the windows to 1285,0 might work. If not let me know and we can try something else.

---

### Post by rickcr on 2008-07-01
Thanks!
It's working great now!
 
I vote for this being included in the distro somewhere. It's extremely useful. I don't know what I'd do without it (other than having to remember to move everything before I leave work for the day.)

---

