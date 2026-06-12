---
title: "Can not run Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by etank on 2007-10-20
I have tried numerous times with both the LiveCD and Alternate CD to install Gutsy on my Dell Inspiron 5150. The install completes but I do not get a desktop. I once got to the login screen but could not type. I booted to single user mode and ran "startx" and got to the desktop but then the system froze. The system will run fine from the LiveCD though. What can i do to get it to work.

Thank you for any help that you can provide.

---

### Post by DagMan on 2007-10-20
If you want to try out turning off compiz to see how it would go with that, you'de edit the compiz script so that all the way at the bottom where this is, the very last line of it 
```
${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS
```
Comment out the first part and then right after the || hit return so you have this
```
#${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || 
exec $FALLBACKWM $FALLBACKWM_OPTIONS
```
If this works then you know you have a problem with the desktop effects that's causing it.

I really have no idea if that will be a starting point or not, but since compiz is enabled by default it's a possibiltiy.  I had problems sort of like what you're describing and had to do this and then start the effects just slightly differantly after everything else was up and running.

Worth a shot maybe.  Good Luck.

---

### Post by volty on 2007-10-22
Same problems with a 5150 I just got for free. Most of the time I get the background to the login screen (that odd pinkish color) and it hangs. Every once in a while, I get a login screen. And only once, I actually saw a taskbar appear at the top. But it freezes, every time.

I also tried to do an install with Kubuntu to see if using the KDE desktop would help. No dice.

I'm downloading a Feisty install now, so in 3 hours, we'll see if it works.

[edit] Tried the above suggestion, no change.

---

### Post by etank on 2007-10-23
Someone else recommended turning acpi off. Someone else said to change usplash.conf to be 1024x768.

I have not tried either of these. Right now I am testing Foresight Linux.

---

### Post by volty on 2007-10-23
The issue is the graphics card, without a doubt. Its no longer supported by the fglrx proprietary driver that gutsy installs, and that support is needed to use all the fancy new desktop effects that come bundled with Gutsy.

You can get it to boot, with some trouble, by getting it to run in low-graphics mode, or whatever, but that takes me like 10 mins of trial and error to get to, and is not a reliable way to boot. It runs off the failsave vesa driver, and sucks.

I'll take a look at your linux version as an alternative, or maybe just reinstall feisty, which since it doesnt have all this fancy **** installed on default, may actually work.

---

### Post by volty on 2007-10-26
Fixed!

Detailed in [http://ubuntuforums.org/showthread.php?t=578445](http://ubuntuforums.org/showthread.php?t=578445). :)

---

