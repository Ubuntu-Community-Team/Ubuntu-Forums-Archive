---
title: "Boot Time is Really Slow Waiting for &quot;Hold until boot process finishes&quot;"
date: 2016-12-08
forum: General Help
---

### Post by mastermindg on 2016-12-08
I'm running 16.10...

I'm sitting on the:

```
"A start job is running for Hold until boot process finishes up (10min 25s / no limit) 
```

I can SSH into the machine and I've checked dmesg and other logs and I can't see any indication of a problem.
[B]
How can I determine what the boot process is waiting for?[/B]

---

### Post by mastermindg on 2016-12-08
Turned out to be lightdm and the default greeter...but I'd still like to know how to get a list of pending systemd services.

---

### Post by #&amp;thj^% on 2016-12-08
> **mastermindg said:**
> Turned out to be lightdm and the default greeter...but I'd still like to know how to get a list of pending systemd services.

Thought that might be the case...
I use this but might not be what you are looking for.
My example is
```
systemctl list-units --type=target
UNIT                   LOAD   ACTIVE SUB    DESCRIPTION                
basic.target           loaded active active Basic System               
cryptsetup.target      loaded active active Encrypted Volumes          
getty.target           loaded active active Login Prompts              
graphical.target       loaded active active Graphical Interface        
local-fs-pre.target    loaded active active Local File Systems (Pre)   
local-fs.target        loaded active active Local File Systems         
multi-user.target      loaded active active Multi-User System          
network.target         loaded active active Network                    
nss-user-lookup.target loaded active active User and Group Name Lookups
paths.target           loaded active active Paths                      
remote-fs.target       loaded active active Remote File Systems        
slices.target          loaded active active Slices                     
sockets.target         loaded active active Sockets                    
sound.target           loaded active active Sound Card                 
swap.target            loaded active active Swap                       
sysinit.target         loaded active active System Initialization      
timers.target          loaded active active Timers                     

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.
17 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.


```
So maybe something like this:
```
systemctl list-unit-files
```
A good site for systemd found here: [URL="https://www.dynacont.net/documentation/linux/Useful_SystemD_commands/"]https://www.dynacont.net/documentation/linux/Useful_SystemD_commands/
[/URL]
Hope this is useful.
EDIT: I think this might be more useful in finding as you say "Pending" Services.
```
systemctl list-units --all
```
Which will show as:
```
inactive dead 
active   exited
active   active
active   running 
active   waiting 
```
And Things Highlighted in Red should be noted...as possible further action needed by user.

---

