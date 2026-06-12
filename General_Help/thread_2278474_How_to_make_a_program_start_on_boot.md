---
title: "How to make a program start on boot"
date: 2015-05-16
forum: General Help
---

### Post by cable_guy on 2015-05-16
hi all,

I would like my application "mythtvbackend" to start on boot, but I can't think what I need to do. 

I know it's not a "service" as such, as all I need to type is simply "mythbackend" So I don't think it's a init.d thing.

thanks for any advice!

---

### Post by monkeybrain20122 on 2015-05-16
Can you just add it to Startup Applications?

---

### Post by nerdtron on 2015-05-16
If you need the full path of the program to add it on the startup applications, run the which command:

"which mythtvbackend"

---

### Post by Keith_Helms on 2015-05-16
On my system, mythbackend has started automatically since I installed it.  I don't remember doing anything special to get it to do that.  I poked around and there is a file under /etc/init called mythtv-backend.conf that looks like it controls the autostarting.  I believe that means it's controlled by upstart.

---

### Post by nerdtron on 2015-05-17
Have you tried:
```
sudo  update-rc.d mythtvbackend defaults 
```

or
```
sudo  update-rc.d mythtvbackend enable 
```

reboot and see if upstart started mythtv

---

### Post by cable_guy on 2015-05-17
> **nerdtron said:**
> Have you tried:
```
sudo  update-rc.d mythtvbackend defaults 
```

or
```
sudo  update-rc.d mythtvbackend enable 
```

reboot and see if upstart started mythtv

Thanks for this, I tried it but it says [B]update-rc.d: /etc/init.d/mythtvbackend: file does not exist
[/B]
> **monkeybrain20122 said:**
> Can you just add it to Startup Applications?

Thanks but you may have to expand for me please, I am a fair noob when it comes to these things, and I only tend to use the command line.

---

### Post by dino99 on 2015-05-17
Thanks for this, I tried it but it says [B]update-rc.d: /etc/init.d/mythtvbackend: file does not exist
[/B]
 [COLOR="#008000"]from post #3 above, run > which mythtvbackend to get the real path[/COLOR]

---

### Post by SeijiSensei on 2015-05-17
> **Keith_Helms said:**
> On my system, mythbackend has started automatically since I installed it.  I don't remember doing anything special to get it to do that.  I poked around and there is a file under /etc/init called mythtv-backend.conf that looks like it controls the autostarting.  I believe that means it's controlled by upstart.

+1

If it's controlled by upstart, you need to examine that file in /etc/init rather than the traditional SysV /etc/init.d or /etc/rc.d.

---

### Post by cable_guy on 2015-05-23
hi guys  still confused on this im afraid.... i know my mythbackend executable is in /usr/bin but i cant work out how to add that to start automatically.i dont know what 'upstart' is

---

