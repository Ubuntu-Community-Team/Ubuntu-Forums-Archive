---
title: "Bootup Error with Conky"
date: 2013-08-25
forum: General Help
---

### Post by TedinOz on 2013-08-25
Hi all. A problem that I can't solve. I am running Ubuntu 12.04 with Conky Lua installed. Whenever I boot up from scratch or restart, Conky loads on my desktop with a permanent solid border on my desktop which stays above all other applications and I cant find a way to remedy it other than by logging out and logging back in. After a re-login the I get a 'New Resolution' popup from Jupiter which I also have running but the Conky display no longer has the border and stays below when I run other applications. 
Screenshots are attached
 
[IMG][[IMG]http://img4.imageshack.us/img4/1005/rxnq.th.png[/IMG]]("http://img4.imageshack.us/i/rxnq.png/")[/IMG]                                    [IMG][[IMG]http://img443.imageshack.us/img443/5834/oumc.th.png[/IMG]]("http://img443.imageshack.us/i/oumc.png/")[/IMG]                  [IMG][[IMG]http://img713.imageshack.us/img713/3558/7oz1.th.png[/IMG]]("http://img713.imageshack.us/i/7oz1.png/")[/IMG]

Wondering now if anyone else has experienced this and if a solution may be available. I'm not sure what log files to run and show here for error detection. Can someone guide me on this?
 
Thanks in advance  :)

---

### Post by stinkeye on 2013-08-25
Try delaying the start of conky at boot.
Use the in built **-p secs** option (or add a sleep command to a start script).....
eg
```
conky -p 30
```

or
```
conky -p 30 -c [COLOR="#808080"]/path/to/conky/config[/COLOR]
```

How are you starting conky at the moment?
Need further help ....post your conky config.

---

### Post by TedinOz on 2013-08-25
> **stinkeye said:**
> Try delaying the start of conky at boot.
Use the in built **-p secs** option (or add a sleep command to a start script).....
eg
```
conky -p 30
```

or
```
conky -p 30 -c [COLOR=#808080]/path/to/conky/config[/COLOR]
```

How are you starting conky at the moment?
Need further help ....post your conky config.

Thanks for early response. What you offer is a bit advanced for me and not sure how to proceed with that. atm conky is added to start up applications to commence at boot.

---

### Post by stinkeye on 2013-08-25
If your command in startup applications for conky is...
```
conky
```

change it to ...
```
conky -p 30
```

Reboot... see what happens.

---

### Post by TedinOz on 2013-08-26
> **stinkeye said:**
> If your command in startup applications for conky is...
```
conky
```

change it to ...
```
conky -p 30
```

Reboot... see what happens.

Thanks...but no joy with this. Conky restarts on re-boot after this change but the same as before. Before this, the only command that worked that I was using was ```
/home/tioz/.conky-startup.sh
``` The content of conky-startup.sh. here is #!/bin/bashsleep 30 && conky ;

Can I do anything to apply your thinking with this?

---

### Post by stinkeye on 2013-08-26
> **TedinOz said:**
> Thanks...but no joy with this. Conky restarts on re-boot after this change but the same as before. Before this, the only command that worked that I was using was ```
/home/tioz/.conky-startup.sh
``` The content of conky-startup.sh. here is #!/bin/bashsleep 30 && conky ;

Can I do anything to apply your thinking with this?
Not familiar with jupiter but the key here may be jupiter changing your resolution after conky has started.
Test without jupiter running.

It appears you are already using a script with the sleep command, delaying the start of conky.
The reason you delay is to give the window manager time to load when booting.

Does your desktop take a long time(over 30 secs) to load from a reboot?
Does conky load okay if you just log out then back in? (log out/in loads desktop quicker than a reboot) 
As a test disable the conky entry in startup applications, reboot and as soon as the desktop has loaded, start conky manually in 
the terminal with simply...
```
conky
```

If that conky loads fine,  replace your **/home/tioz/.conky-startup.sh** command to start conky in startup applications with..
```
conky -p 30
```

If your desktop takes a long time to load increase the **-p [COLOR="#FF0000"]30[/COLOR]** value.

Also post your config from **/home/tioz/.conkyrc**
It may be as simple as changing **own_window_type**

---

### Post by TedinOz on 2013-08-26
> **stinkeye said:**
> Not familiar with jupiter but the key here may be jupiter changing your resolution after conky has started.
Test without jupiter running.

It appears you are already using a script with the sleep command, delaying the start of conky.
The reason you delay is to give the window manager time to load when booting.

Does your desktop take a long time(over 30 secs) to load from a reboot?
Does conky load okay if you just log out then back in? (log out/in loads desktop quicker than a reboot) 
As a test disable the conky entry in startup applications, reboot and as soon as the desktop has loaded, start conky manually in 
the terminal with simply...
```
conky
```

If that conky loads fine,  replace your **/home/tioz/.conky-startup.sh** command to start conky in startup applications with..
```
conky -p 30
```

If your desktop takes a long time to load increase the **-p [COLOR=#FF0000]30[/COLOR]** value.

Also post your config from **/home/tioz/.conkyrc**
It may be as simple as changing **own_window_type**
 
Ok! I increased the value to 45 and that worked fine...so no need to post further configs. Thank you...and thanks for helping me understand.
Thanks also to these very valuable forums.

---

### Post by stinkeye on 2013-08-26
OK ,good.
Just FYI.
IN your conky config (/home/tioz/.conkyrc) you will have a setting...
```
own_window_type
```

I always use 
own_window_type **normal**

Others like to use
own_window_type **override**
because it stops compiz drawing a shadow around conky.
This can cause problems though because
override windows are not under the control of the window manager.

So I use...
```
own_window_type **normal**
```
and use compizconfig-settings-manager to disable the shadow as shown in pic.

```
(any) & !(class=Conky)
```

---

### Post by TedinOz on 2013-08-26
> **stinkeye said:**
> OK ,good.
Just FYI.
IN your conky config (/home/tioz/.conkyrc) you will have a setting...
```
own_window_type
```

I always use 
own_window_type **normal**

Others like to use
own_window_type **override**
because it stops compiz drawing a shadow around conky.
The override setting can have other problems though.

So I use...
```
own_window_type **normal**
```
and use compizconfig-settings-manager to disable the shadow as shown in pic.

```
(any) & !(class=Conky)
```

Thanks for that. You continue to add to my learning processes. You were right...my (/home/tioz/.conkyrc) does have the **override **setting so I will follow your lead. No other problems seem apparent at this point but all this is good to know. 

Thanks again!

---

