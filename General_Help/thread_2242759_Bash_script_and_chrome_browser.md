---
title: "Bash script and chrome browser"
date: 2014-09-03
forum: General Help
---

### Post by marx404 on 2014-09-03
I made a bash script that opens the terminal, opens chrome browser and then runs a few bleachbit commands and closes afterwards when I close my browser. As follows:

> 
#!/bin/bash/usr/bin/google-chrome-stable %U
bleachbit -c google_chrome.cache
bleachbit -c google_chrome.cookies
bleachbit -c google_chrome.history 


I had a similar windows batch file for CCleaner. This bash file seems to work fine, but I get the following error messages when the script initially runs:

> 
Gtk-Message: Failed to load module "overlay-scrollbar"
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[20457:20457:0903/205137:ERROR:sandbox_linux.cc(308)] InitializeSandbox() called with multiple threads in process gpu-process
[20416:20416:0903/205137:ERROR:desktop_window_tree_host_x11.cc(1478)] Not implemented reached in void views:desktopWindowTreeHostX11::MapWindow(ui::WindowShowState)


I hope that this is not really a chrome issue, but what exactly is breaking here and is the sandboxing in chrome browser being affected? How do I fix this?
Pardon, but just learning bash scripting.

Thanks, marx404

---

### Post by varunendra on 2014-09-04
> **marx404 said:**
> > **#!/bin/bash**[COLOR="#FF0000"]/usr/bin/google-chrome-stable %U[/COLOR]
Is that just a typo in your post here (maybe copy-paste glitch) or really the first line of your script?

The sha-bang (#!) line is supposed to contain ONLY your desired shell interpreter, not a full command or anything else. If it is messed up as above, it would default to 'sh' instead of whatever you intend to use as the interpreter ('bash' in your case).

In short, it should be broken into two lines -
```
#!/bin/bash
/usr/bin/google-chrome-stable %U
```

If it is already that way, and it is just a typo here, then I've no idea what may be wrong.

---

### Post by vasa1 on 2014-09-04
I don't know whether deleting stuff using an external program while the browser is open is a good thing. Why do you need to open the browser in the first place? Is that a requirement of bleachbit?

---

### Post by sisco311 on 2014-09-04
Unless chrome starts in the background by default, bleachbit will run after the browser process started in the script terminates. However other instances of chrome still running will be affected.

@OP:

If chrome works for you as intended regardless of the warnings/errors then you can ignore them. After all, they were ignored (considered noncritical) by programmers too. ;)

 I don't use chrome, but a quick google search revealed that it has an incognito mode. Did you try it instead of using bleachbit?


Oh, and %U is used in .desktop files (launchers/menu entries) not in scripts. In a .desktop file %U will expand to a list of URLs, but in your script %U will be passed as an argument to the app literally.

---

### Post by marx404 on 2014-09-04
> **varunendra said:**
> Is that just a typo in your post here (maybe copy-paste glitch) or really the first line of your script?

The sha-bang (#!) line is supposed to contain ONLY your desired shell interpreter, not a full command or anything else. If it is messed up as above, it would default to 'sh' instead of whatever you intend to use as the interpreter ('bash' in your case).

In short, it should be broken into two lines -
```
#!/bin/bash
/usr/bin/google-chrome-stable %U
```

If it is already that way, and it is just a typo here, then I've no idea what may be wrong.

Yes, that was a error caused by copy/paste I did not catch, they are actually on two lines as should be. ;)

To clarify, chrome browser doesn't clean up after itself after you close it. Bleachbit is a privacy cleaner that can run in command line mode. 
The objective is for the script to run, which opens chrome browser. Then the script (terminal) remains open in the background until I close chrome browser. AFTER I close chrome browser, the script runs the three commands in Bleachbit to clean house.

The script works fine, but my main concern is the error messages. Is chrome browser's Sandbox getting disabled or broken? Should I interpret the error message that way?
Thanks.

---

