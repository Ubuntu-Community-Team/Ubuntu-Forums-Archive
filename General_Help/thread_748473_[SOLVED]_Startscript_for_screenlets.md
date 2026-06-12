---
title: "[SOLVED] Startscript for screenlets"
date: 2008-04-07
forum: General Help
---

### Post by Benjamin_Vedder on 2008-04-07
Hello

I want to make script to start my screenlets manually from my desktop. The reason i dont want to autostart them is because they wont run well when compiz is turned off. But, when compiz is on games run slower and movies look worse (tearing). 

So, when i use my computer for work with eclipse, open office etc. i want to run compiz and just doubleclick om my script to run my screenlets, and when i play games or watch movies i use my conky script.

That sounds simple, but im very very new to bash scripting, so i ran into a problem:

i wrote something very simple:

```

#!/bin/sh

python -u /home/benjamin/.screenlets/Sidebar/SidebarScreenlet.py
python -u /usr/share/screenlets/ACPIBattery/ACPIBatteryScreenlet.py
python -u /usr/share/screenlets/Clock/ClockScreenlet.py
python -u /usr/share/screenlets/Diskusage/DiskusageScreenlet.py
python -u /home/benjamin/.screenlets/Netmon/NetmonScreenlet.py
python -u /usr/share/screenlets/Sensors/SensorsScreenlet.py
python -u /home/benjamin/.screenlets/Wireless/WirelessScreenlet.py

```

When i run the script the sidebar appears, but nothing else. When i close the sidebar the battery appears, and when i close the battery the clock appears and so on. That is because the script executes one command at the time, and wont go on with the next one beforel the current one has finished.

So, is there some way to make the script start all at once, or maybe a totally different way to make this work?

---

### Post by y-lee on 2008-04-07
Try putting  an **& ** at the end of each line. it is my understanding that should work, but I'm no linux guru. Let us know if that works.

---

### Post by Benjamin_Vedder on 2008-04-07
Great :) That did it! thanks y-lee

---

