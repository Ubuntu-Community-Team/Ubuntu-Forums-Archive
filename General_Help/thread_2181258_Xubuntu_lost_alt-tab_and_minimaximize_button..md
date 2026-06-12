---
title: "Xubuntu lost alt-tab and mini/maximize button."
date: 2013-10-17
forum: General Help
---

### Post by kruget on 2013-10-17
After updating Xubuntu few weeks ago my Xubuntu lost the alt-tab function, it also lost the buttons to minimize, maximize and close app. 

Please help, what should i do to fix it?

---

### Post by Toz on 2013-10-17
Alt+F2 and run the following command:
```
xfwm4 --replace
```

---

### Post by kruget on 2013-10-18
> **Toz said:**
> Alt+F2 and run the following command:
```
xfwm4 --replace
```

Thank You, it solved my problem. 

Unfortunately after reboot it happened again so i have to redo it every time. 
Is there any way to cure this weirdness completely? 
I also wonder what caused it.

---

### Post by Adam_GUI on 2013-10-18
> **kruget said:**
> Thank You, it solved my problem. 

Unfortunately after reboot it happened again so i have to redo it every time. 
Is there any way to cure this weirdness completely? 
I also wonder what caused it.

Settings > Settings Manager > Session & Startup > Application Autostart > add > Command field > xfwm4 --replace

Did you install compiz per chance?
It sounds as if it it got installed.

If you have it, run "ccsm".
If it isn't installed, "sudo apt-get install compizconfig-settings-manager".
I'd check your settings for "Place", "Move Window", "Resize Window", and "Shift Switcher".

Compiz effects never played nice with XFWM for me.  
So, I had to rely on installing emerald to have min, max, and exit window border buttons.

Forcing the xfwm --replace will give control of the window manager and effects back to xfce with no fancy effects.
So, adding that to startup means you can skip the compiz instructions I just typed out.

---

### Post by kruget on 2013-10-19
> **Adam_GUI said:**
> Settings > Settings Manager > Session & Startup > Application Autostart > add > Command field > xfwm4 --replace

Did you install compiz per chance?
It sounds as if it it got installed.

If you have it, run "ccsm".
If it isn't installed, "sudo apt-get install compizconfig-settings-manager".
I'd check your settings for "Place", "Move Window", "Resize Window", and "Shift Switcher".

Compiz effects never played nice with XFWM for me.  
So, I had to rely on installing emerald to have min, max, and exit window border buttons.

Forcing the xfwm --replace will give control of the window manager and effects back to xfce with no fancy effects.
So, adding that to startup means you can skip the compiz instructions I just typed out.

I don't have compiz installed. I hate fancy effect, that is why i use Xubuntu and xfce.

The start up trick solve my problem. Thank You very much.
I'll mark this as solved.

---

### Post by Toz on 2013-10-19
The other way to do this, so you don't have to create a startup item for xfwm4, is to clear the sessions cache (Settings Manager -> Sessions and Startup -> Sessions Tab -> Clear Saved Sessions). On the next log in, Xfce will create a new session which will include all of the base Xfce components including xfwm4.

Note: In previous versions of Xfce, you had to logout of the session and from a text console (Ctrl+Alt+F1), delete the contents of ~/.cache/sessions. This new functionality in 4.10 should replace the need for this, but in case it doesn't work (I haven't been in a position to test it yet) you may need to do it this old way.

---

### Post by vasa1 on 2013-11-28
> **Toz said:**
> The other way to do this, so you don't have to create a startup item for xfwm4, is to clear the sessions cache (Settings Manager -> Sessions and Startup -> Sessions Tab -> Clear Saved Sessions). On the next log in, Xfce will create a new session which will include all of the base Xfce components including xfwm4.

Note: In previous versions of Xfce, you had to logout of the session and from a text console (Ctrl+Alt+F1), delete the contents of ~/.cache/sessions. This new functionality in 4.10 should replace the need for this, but in case it doesn't work (I haven't been in a position to test it yet) you may need to do it this old way.
@Toz, someone else had a problem with the session information being retained. I suggested the first (GUI) option but that apparently didn't work whereas [the console route seems to have worked]("http://askubuntu.com/q/382331/25656").

---

### Post by Toz on 2013-11-29
> **vasa1 said:**
> @Toz, someone else had a problem with the session information being retained. I suggested the first (GUI) option but that apparently didn't work whereas [the console route seems to have worked]("http://askubuntu.com/q/382331/25656").

I've seen that as well on occasion and I don't know what the trigger is. The console route seems to be the sure-fire method where as the gui route I find is effective about 90% of the time. I wonder whether on logout somehow the corrupted session is getting saved again? Maybe they "saved sessions" checkbox is checked on the logout dialog or within the Settings Manager that is doing this? Haven't been able to find out for sure though.

---

