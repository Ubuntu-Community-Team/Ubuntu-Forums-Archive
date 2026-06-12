---
title: "Restart: yes, shutdown: no. Why?"
date: 2008-02-17
forum: General Help
---

### Post by ChristosG on 2008-02-17
I had XP and I installed Ubuntu too, and when I restart from Ubuntu, everything is normal, when in Ubuntu and I try to shut down my pc, when the orange bar gets empty, my pc doesn't turn off, it stucks at this point, so I have to restart my pc, boot from XP and shut it down from there. How can I solve this?

---

### Post by confused57 on 2008-02-17
> **ChristosG said:**
> I had XP and I installed Ubuntu too, and when I restart from Ubuntu, everything is normal, when in Ubuntu and I try to shut down my pc, when the orange bar gets empty, my pc doesn't turn off, it stucks at this point, so I have to restart my pc, boot from XP and shut it down from there. How can I solve this?
Have you tried opening a terminal?:
```
sudo shutdown -h now
```

You might also try adding this line to your /etc/modules:
```
gksudo gedit /etc/modules
```
add this line to the file:
```
apm power_off=1
```
quit & save

---

### Post by russell.h on 2008-02-17
Is your computer really old?

A long time ago power supplies couldn't be controlled in software, so the operating system would put a  message on the screen saying "It is now safe to turn off your computer" or something similar. Does XP do that?

---

### Post by ZxEfR on 2008-02-17
> **ChristosG said:**
> I had XP and I installed Ubuntu too, and when I restart from Ubuntu, everything is normal, when in Ubuntu and I try to shut down my pc, when the orange bar gets empty, my pc doesn't turn off, it stucks at this point, so I have to restart my pc, boot from XP and shut it down from there. How can I solve this?

This happens to me too....it's just the fact that the Linux kernel isn't that great at handling PC power systems yet.......all you have to do is just power down at that point....the OS has been unloaded at that point.....no need to boot back into windows.....it's somewhat of a pain. Linux is friggin awesome but it's still a baby....won't be much longer and stuff like this will be a thing of the past :popcorn:

I'm gonna try confused57's suggestion though.... UPDATE: It didn't work for me :O(

---

### Post by wolfen69 on 2008-02-17
try 
```
sudo halt
```

---

### Post by ChristosG on 2008-02-17
> **wolfen69 said:**
> try 
```
sudo halt
```

it worked :)

---

### Post by ZxEfR on 2008-02-17
Power down fully is working for me now :)

With a little search I came across this --- [http://ubuntuforums.org/showthread.php?t=698972](http://ubuntuforums.org/showthread.php?t=698972)

I am using 'apm power_off=1' in the modules file. But in order for the apm line to work you gotta make sure you start apm as it's off by default.

You have to add 'apm=on' to your boot loader file.....I am not using 'acpi=force' however.

---

### Post by kokerkov on 2008-07-15
> **confused57 said:**
> Have you tried opening a terminal?:
```
sudo shutdown -h now
```

You might also try adding this line to your /etc/modules:
```
gksudo gedit /etc/modules
```
add this line to the file:
```
apm power_off=1
```
quit & save

Thank you,dude!It really works!I've tried "acpi=on/off noapci" before.None of  them works.In one word-thx!

---

