---
title: "How to execute a script on logut in Ubuntu 14.04"
date: 2015-03-06
forum: General Help
---

### Post by squirrel2003 on 2015-03-06
[http://askubuntu.com/questions/293312/execute-a-script-upon-logout-reboot-shutdown-in-ubuntu](http://askubuntu.com/questions/293312/execute-a-script-upon-logout-reboot-shutdown-in-ubuntu)

In this thread it gets explained where to put a script so it executes everytime one logs out of ubuntu.

The file **/etc/lightdm/lightdm.conf  **is missing in my installation of Ubuntu 14.04.

Where is i gone?
Wehere can i paste the line session-cleanup-script=/path/to/script to execute the script i created on logout.

Thanks if you helping.

---

### Post by ian-weisser on 2015-03-06
What kinds of cleanup do you envision?

Do-an-action-upon-logout may be unreliable, because some sessions end without a logout.
Power failures, hardware failures, and several kinds of crashes may end a session. Sometimes merely resetting the X server, other times causing real grief.

One answer:
In 14.04, systemd-logind (provided by the libsystemd-login0 package) emits a dbus signal when a session logs in or out.
You can easily write a listener for those signals. It may need a little logic to read the signal and determine if it should launch the script.

---

### Post by CantankRus on 2015-03-07
Not sure if this still works but from my notes.... "In 14.04 add to /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf"
```
gksudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
```
You will probably need to restart to reload lightdm, then your session-cleanup-script should work on next logout.

---

### Post by squirrel2003 on 2015-03-07
> **ian-weisser said:**
> What kinds of cleanup do you envision?

Do-an-action-upon-logout may be unreliable, because some sessions end without a logout.
Power failures, hardware failures, and several kinds of crashes may end a session. Sometimes merely resetting the X server, other times causing real grief.

One answer:
In 14.04, systemd-logind (provided by the libsystemd-login0 package) emits a dbus signal when a session logs in or out.
You can easily write a listener for those signals. It may need a little logic to read the signal and determine if it should launch the script.

What i want to achieve is that a script running ```
sdmem -llfv
``` will execute upon logout.
The idea behind it is to install ubuntu to a thumbdrive withan encrypted home partition. Before i leave the house i shut down my netbook, plugin the usb drive, start the system, login, start recording using cheese or motion, logout and leave the house.
This should in my theory prevent an intruder to perform a cold boot attack in order to extract the login password, or the home directory encryption key and perform any changes on my hardware before leaving the appartment and make it look for me as if nothing has happened.
I have read about some special cases in which sdmem would not be able to fully wipe the RAM and one person told me i should try out TRESOR but first i want to finish with this task.




> **CantankRus said:**
> Not sure if this still works but from my notes.... "In 14.04 add to /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf"
```
gksudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
```
You will probably need to restart to reload lightdm, then your session-cleanup-script should work on next logout.

Thank you i will try it the way you described.

---

### Post by squirrel2003 on 2015-03-07
I have edited the 50-unity-greeter.conf adding the line: 
session-cleanup-script=/home/ubunt/Dokumente/Scripts/sdmem.sh      in the end of the file.
Then i saved the file and rebooted.
After entering my login credentials i was presented with a black screen.
I restored my Laptop and  am wondering if i misunderstood something and made a mistake editing the greeter.conf file or what else might cause the failure.
One of the first things i did on this laptop was applying the brightness fix as described in the following link.
[http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)
Could this change cause a problem?

---

### Post by squirrel2003 on 2015-03-09
Anyone?

---

### Post by CantankRus on 2015-03-09
Test something simple to run when you logout.
eg I just use this to clear recent in nautilus
_lightdm-session-cleanup.sh_
```
#!/bin/bash

## Clears Recent in nautilus
echo > /home/[COLOR="#FF0000"]glen[/COLOR]/.local/share/recently-used.xbel
```
Edit for [COLOR="#FF0000"]your username[/COLOR]

and my **/usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf** file...
```
[SeatDefaults]
greeter-session=unity-greeter
session-cleanup-script=[COLOR="#FF8C00"]/home/glen/scripts/lightdm-session-cleanup.sh[/COLOR]
```
Edit for [COLOR="#FF8C00"]path to script[/COLOR]
Check recent in nautilus before and after you logout.

If recent files are cleared, problem is in your original script.
Post the script your using.

---

### Post by squirrel2003 on 2015-03-12
Big thanks for the help [**[COLOR=#000000]CantankRus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1938181") i guess the problem was the -v in the script because it works now without.

#!/bin/bash

sdmem -llf

---

