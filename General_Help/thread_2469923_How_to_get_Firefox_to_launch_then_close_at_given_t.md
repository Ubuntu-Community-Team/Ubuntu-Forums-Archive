---
title: "How to get Firefox to launch then close at given times (Ubuntu 20.04 LTS)"
date: 2021-12-13
forum: General Help
---

### Post by yewoja4247 on 2021-12-13
Good day everyone!

I have a question about getting Ubuntu to make it seem like I am home when away for the holidays. I want to connect it to my TV through eArc and get it to turn on my TV and play some stuff at night then stop when "I go to bed". Basically, I want it to do the following:

- At 17h29, wake up 
- At 17h30, launch Firefox to a given live TV channel
- At 21h45, close Firefox 
- At 21h46, go into suspend 

I have the firefox crontab set up and working, but for the life of me I can't figure out the rest. 
Here is what I found on this forum that works for launching the site: 
```
30 17 * * * export DISPLAY:0 && firefox --new-window http://site.com
```

I can't even manage to find a way to close the firefox window using cron. I have tried every "killall", "pkill".
```
pkill firefox 
killall firefox
sudo kill firefox

```

Any help would be appreciated on the kill part and if possible on the suspend/wake part :) 

Thank you in advance!

---

### Post by KBar on 2021-12-13
Why would you want to kill Firefox? Whenever I want to suspend my laptop, I leave everything as it is and just close its lid. [s]Regardless, **pkill** should do the trick. I'm surprised that it can't in your case.[/s] It looks like you need to specify its parent process, which is GeckoMain. The following command kills Firefox successfully.
```
pkill GeckoMain
```


Another method worth trying is **wmctrl**. 
```
window_id=$(wmctrl -lp | grep 'Firefox' | tr --squeeze-repeats ' ' | cut --delimiter=' ' --fields=1)
wmctrl -ic ${window_id}; exit 0
```

It's even easier if the Firefox window is the active window. 
```
wmctrl -c :ACTIVE:
```

This won't work if Firefox is set to prompt for confirmation on exit.

The command for suspend is```
systemctl suspend
```You can place a script in */lib/systemd/system-sleep* that will launch Firefox on wake-up. It would look something like this:
```
#!/bin/bash

if [[ $1 = post ]]; then
        firefox --new-window http://site.com;
fi
```

This one is not POSIX-compliant. You can also do it with **case**.

Care to share the full details and instructions, i.e. how exactly did you do the waking-up or turning-on part?

Don't forget to mark your thread as solved afterwards. Thanks.

[HR][/HR]**pkill**(1), **wmctrl**(1), **systemd-sleep**(8)

---

### Post by Holger_Gehrke on 2021-12-13
A decidedly lower-tech solution would be one of those timer-controlled TV-Simulators (basically a couple of strong LEDs and a bit of circuitry to switch them at random). Depending on the device it can switch on at darkness or at a given time and can be set to run for a given time. Should need less energy than a PC and a TV and can be had for around &#8364; 15.

Holger

---

### Post by yewoja4247 on 2021-12-13
The *pkill GeckoMain* worked like a charm; thank you!

For the suspend/wake, I was hoping to add additional cron job or other automation to make the system do it automatically. I want it to do it when I am not home for a few days as to simulate the presence of someone. 
So it seems I may be able to use the systemctl suspend to suspend it, but would there be a possibility to automatically wake it up at a certain hour daily?

---

### Post by yewoja4247 on 2021-12-13
I actually tried one of those and it looks really fake to me at least. If I watch it for longer than 20sec, I can see the abnormal flickering and it makes me think of a tube TV :D 
Plus, no sound. I would love to have the sound too for added sharade

---

### Post by dragonfly41 on 2021-12-13
Try writing a script in Actiona GUI (it is like AutoHotKey in Windows)

sudo apt install actiona

[https://github.com/Jmgr/actiona](https://github.com/Jmgr/actiona)

The GUI is for developing your script.

Then if the script is saved as say Timer.ascr (it uses ancient Qt4 objects and Actionscript2) you can start it (without GUI) by running
actexec Timer.ascr

actexec sits alongside actiona in /usr/bin/

You can also mix it with commands such as xdotool.
You can randomise time variables.

Or you might experiment with Zapier.

---

### Post by KBar on 2021-12-13
> **yewoja4247 said:**
> So it seems I may be able to use the systemctl suspend to suspend it, but would there be a possibility to automatically wake it up at a certain hour daily?

I thought you were able to set it up, the OP at least explicitly states so.

To accomplish that, you are going to have to add a new cron job in */etc/cron.d*. There should be a couple of good examples in that directory. 
[HR][/HR]
**cron**(8)

---

### Post by HermanAB on 2021-12-14
Hmm, the olde fashioned brute force UNIX process control methods should still work:

```

#! /bin/bash
firefox [http://www.cnn.com](http://www.cnn.com) &
PID=$!
sleep 10
kill $PID

```

---

