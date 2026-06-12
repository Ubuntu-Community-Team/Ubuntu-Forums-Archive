---
title: "Stop laptop from shutting off when i flip the lid down in ubuntu"
date: 2020-06-04
forum: General Help
---

### Post by dellboy on 2020-06-04
Hi there I have ubuntu 20.04lts install on an old but good laptop that I want to leave on in the day off work acting as a mini server for a few simple tasks but I would like to be able to close the lid down on the laptop and still have it running

but at the moment it seems to shut itself off when I flip the lid down i have tried setting it  i have run the following command in the terminal and set HandleLidSwitchDocked=ignore but it still not doing as told is there anythink else i need to be doing to make this happen 

thanks for your help

sudo gedit /etc/systemd/logind.conf


Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
#InhibitDelayMaxSec=5
#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
#HandleLidSwitch=ignore
#HandleLidSwitchExternalPower=suspend
#HandleLidSwitchDocked=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=ignore
#HoldoffTimeoutSec=30s
#IdleAction=ignore
#IdleActionSec=30min
#RuntimeDirectorySize=10%
#RemoveIPC=yes
#InhibitorsMax=8192
#SessionsMax=8192

---

### Post by sdsurfer on 2020-06-04
I know you said tried setting it, but did you try
System Settings (not "Settings") -> Power -> When List is Closed set to "Nothing" when plugged in?

---

### Post by ajgreeny on 2020-06-04
I do not make that setting using the /etc/systemd/logind.conf file but use the ***xfce4-power-manager*** settings as I'm using Xubuntu.

However, I note that your file has all lines commented out, with # at the start.  I'm not sure if systemd uses the same syntax as most config files do but it may be worth removing that # from the line in question to see if that does the trick.

---

### Post by dellboy on 2020-06-04
> **sdsurfer said:**
> I 
System Settings (not "Settings") -> Power -> When List is Closed set to "Nothing" when plugged in? 
Could not find any other settings at all 

But i managed to fix this was a bit off a  mistake but i removed the # and it worked not sure why I did not notes this that they where all commented out 

but here is the solution if anyone else needs it

---

### Post by ajgreeny on 2020-06-05
Great!
Please mark as SOLVED from the thread tools menu up top. It's  a great help to others searching the forum.

---

