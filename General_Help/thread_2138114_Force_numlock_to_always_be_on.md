---
title: "Force numlock to always be on"
date: 2013-04-23
forum: General Help
---

### Post by pokepal101 on 2013-04-23
_***SOLVED! Thanks!***_
```
#!/bin/bash
while true; do
sleep 1
numlockx on
done
exit 0
```

Is there any way I can force numlock to be 'always-on'?
I'd like this because the only thing I use my numpad for is entering numbers, and it bothers me whenever I try to type something into a spreadsheet and it completely screws up.

On Windows, I have an AutoHotKey script that automatically toggles numlock whenever it turns off.
Is there a comparable alternative for Linux?

Thanks in advance.

---

### Post by Doug S on 2013-04-23
Typically, the keyboard num lock bootup state is a BIOS setting.

---

### Post by pokepal101 on 2013-04-23
> **Doug S said:**
> Typically, the keyboard num lock bootup state is a BIOS setting.

Uh... no.
I'm fully aware that I can easily change the ***default*** numlock state, but often I accidentally tap the num-lock key, or something screws up and num-lock resets itself.
I want num-lock to be ***always*** on regardless of whatever happens. I want it so that the ***only*** way num-lock will ***ever*** be off is if I forcibly terminate this 'num-lock enforcer' program.
Like with my AHK script:
```
SetTimer, EnforceNumLock, 500 
Return 
 
EnforceNumLock: 
   NumLockStatus := GetKeyState("Numlock", "T") 
    IfEqual, NumLockStatus, 0 
      { 
      SetNumLockState, On 
      } 
Return 
```

---

### Post by stinkeye on 2013-04-23
You can set numlock on using numlockx.
```
sudo apt-get install numlockx
```

Then use something like this to turn numlock on every 5secs 

```
#!/bin/bash

while true; do
sleep 5

numlockx on

done
exit 0
```

---

### Post by SifGrey on 2013-04-23
I was about to post a thread similar to this one so thanks pokepal101 and stinkeye.

---

### Post by pqwoerituytrueiwoq on 2013-04-23
> **Doug S said:**
> Typically, the keyboard num lock bootup state is a BIOS setting.it always gets turned off during the boot process, setting default via lightdm start script works better

you can use this in a cronjob
```
*/5 * * * * env DISPLAY=:0.0 /usr/bin/numlockx on
```
that is set for every 5 minutes

edit:
set this as a keyboard shortcut for Num_Lock
```
sh -c 'sleep 0.5;numlockx on'
```
it works on xubuntu here

---

### Post by pokepal101 on 2013-04-24
> **stinkeye said:**
> You can set numlock on using numlockx.
```
sudo apt-get install numlockx
```

Then use something like this to turn numlock on every 5secs 

```
#!/bin/bash

while true; do
sleep 5

numlockx on

done
exit 0
```

It works! Thanks! This was exactly what I was looking for!

---

