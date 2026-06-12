---
title: "Putting monitor in standby - with framebuffer"
date: 2007-09-24
forum: General Help
---

### Post by jimdaddy on 2007-09-24
Hey guys,

I have a really stripped down embedded linux device which has a built in touch screen monitor (with not on/off switch etc) which is running an app over framebuffer.

I was wondering if anyone knew what options I might have for turning the monitor on/off based on activity, or even a program which could turn it on or off, enable/disable standby etc. I know of `xset dpms` which obviously requires Xorg so it won't be of any use to me.

Any suggestions are appreciated :)

Cheers,

---

### Post by mali2297 on 2007-09-24
I haven't tried it myself, but I recently stumbled upon **setterm**. From **man setterm**:
> 
       -blank [0-60] (virtual consoles only)
              Sets the interval of inactivity, in minutes, after which the
              screen  will  be  automatically blanked (using APM if avail-
              able).  Without an argument, defaults to 0 (disable  console
              blanking).

....


       -powersave on|vsync
              Puts the monitor into VESA vsync suspend mode.

       -powersave hsync
              Puts the monitor into VESA hsync suspend mode.

       -powersave powerdown
              Puts the monitor into VESA powerdown mode.

       -powersave [off]
              Turns off monitor VESA powersaving features.

       -powerdown [0-60]
              Sets the VESA powerdown interval  in  minutes.   Without  an
              argument, defaults to 0 (disable powerdown).  If the console
              is blanked or the monitor is in suspend mode, then the moni-
              tor  will  go  into  vsync  suspend  mode  or powerdown mode
              respectively after this period of time has elapsed.


---

### Post by jimdaddy on 2007-09-24
Thanks for the reply! The app setterm is on the box already so that's a big bonus.

Trying to run it however I get the error:

> 
root@(none):~# setterm -blank 1
'xterm': unknown terminal type.


my $TERM is set as xterm since I have to ssh into the box (no keyboard/mouse etc). How can I set this to whatever term the machine is running ?

Thanks again!

---

### Post by mali2297 on 2007-09-24
> **jimdaddy said:**
> 
my $TERM is set as xterm since I have to ssh into the box (no keyboard/mouse etc). How can I set this to whatever term the machine is running ?


Try 
```

setterm -term console -blank 1

```

..or run ssh from one of your virtual consoles.

---

### Post by jimdaddy on 2007-09-25
Thanks :) It seems the term name is "linux". I wont be able to test if it worked just yet, hope it did! Do you know if there would be any problem with having dual monitors on that machine?

---

