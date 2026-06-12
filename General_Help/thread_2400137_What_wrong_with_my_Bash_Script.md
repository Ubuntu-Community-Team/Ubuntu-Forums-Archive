---
title: "What wrong with my Bash Script?"
date: 2018-09-03
forum: General Help
---

### Post by webmiester on 2018-09-03
Hi Everyone,

Can you please help me?

I made this Bash script which should load upon log-in:

#!/bin/bash
sleep 40
pkill -HUP xbindkeys
xbindkeys -f /home/user/Desktop/.xbindkeysrc
xmodmap -e "clear Control"
xmodmap -e "add Control = 0xff13"
xmodmap -e "keysym 0x60 = 0x0f1"
xmodmap -e "pointer = 1 2 99"
chromium 
numlockx on
xset s 0 0
xset s off


What this script does is that it disables the control buttons and remaps it somewhere else.  Then it uses xbindkeys to assign specific Control+key combinations to other keys.  Then it disables the right click button, it sets number lock on, removes the screensaver and loads chromium.

Each line works on the terminal when entered by itself,  but when I reboot and it runs that bash script upon boot up, it appears that the only lines that work are the following lines.  Everything else fails :(

xmodmap -e "clear Control"
xmodmap -e "add Control = 0xff13"

When I test each line in a command line, they work fine.  Lastly, when I load the script from the command line, it also works fine.  Its only in bootup that it seem to choose to run only these 2 lines.

I already placed 40 seconds sleep so that the system can complete to do other things before the rest of the script launches.  But I still dont get why the lines dont seem to work.  I chenged this to 20 seconds but still got the same response.

Thanks a plenty.  I hope to hear from you guys,

---

### Post by SeijiSensei on 2018-09-03
How is this script run?  From .bashrc?

What if you remove the line that invokes Chromium?  If the network is not yet up, as happens routinely in Ubuntu as it waits for you to specify a wifi access point, then it could be hanging on that.

---

### Post by webmiester on 2018-09-03
Thanks.

You are right.  I reviewed the startup applications and I didn't find my script there.
I supposedly placed it in the "Startup Applications" program, the GUI one.

In the same startup applications list, I found the 2 lines of this script were actually inserted there.
So I kept trying to figure out why only those 2 lines "from my script" were loading when in fact my script wasn't even loading at all and that those 2 "working lines" were actually from a different source.

I really want to thank you guys.  Sometimes I feel kind of dumb on these things.  
I posted this after hours of trying to figure out what was wrong with the script, making changes to it, and several tests, only to find out that the script wasn't even loaded on startup.

Thanks so much.

---

