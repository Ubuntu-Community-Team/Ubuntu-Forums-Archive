---
title: "The Screen on Ubuntu MATE 14.04.2 always goes OFF after 10mins!"
date: 2015-05-29
forum: General Help
---

### Post by amjjawad on 2015-05-29
Hi,

I have an old machine which I use as a Media Center connected to my TV:

[ATTACH=CONFIG]262292[/ATTACH]

Ubuntu MATE 14.04.2 is installed on that machine.

I use it to watch videos and I am having hard time because every time I play something, the screen goes OFF after 10 minutes no matter what I did.

Yes, I did change the power management settings - Nothing happened.
Yes, I did change the settings of the screensaver - Nothing happened.
Yes, I followed:
[http://askubuntu.com/questions/67355/how-do-i-completely-turn-off-screensaver-and-power-management](http://askubuntu.com/questions/67355/how-do-i-completely-turn-off-screensaver-and-power-management)

and via:
```
dconf-editor
```

idle-activation-enabled - disabled

However, still the same.

I usually watch something at night on that machine to relax and go to bed with less stress and thoughts as my days are usually full of stuff so I need to have some peace of mind at night. This machine is giving me hard time so far :(

Truth is, I have less time to keep trying so if anyone has experienced the same issue with his/her machine, I appreciate if he/she has a workaround for this.

I tried last night to remove the screensaver package but didn't want to mess with the system because, to be honest, I have limited experience with MATE desktop. I use Xubuntu and GNOME and not very much used to MATE except on that machine which is used purely for watching movies/videos.

I feel the solution is so simple but my mind is fully occupied at the moment. Sorry if this is silly/simple thing to ask.

Thanks in advance!

P.S.
I remember I had the same issue with Lubuntu on different machine (can't remember which version) and IIRC, the issue wasn't solved until the next release.

---

### Post by kerry_s on 2015-05-29
if it's just the screensaver, go into startup & uncheck it.

---

### Post by amjjawad on 2015-05-29
> **kerry_s said:**
> if it's just the screensaver, go into startup & uncheck it.

[ATTACH=CONFIG]262298[/ATTACH]

Thank you for replying :)

My apology, I should have mentioned that I have done that already but nothing has changed.
That was the first thing I have done after changing:

[ATTACH=CONFIG]262299[/ATTACH]

and this too:

[ATTACH=CONFIG]262300[/ATTACH]


So, any other idea?!

Thank you :)

---

### Post by kerry_s on 2015-05-29
set that screen saver to blank screen.

also i'm using 15.04, not sure if that matters.

in your terminal check " xset q "
screen saver should be 0
&
dpms should be 0

if there not all 0 you can set them in startup, i've done that in the past when i had those kind of issues.

---

### Post by Dennis N on 2015-05-29
With the 10 min time you mention, you probably suffer from the DPMS problem. See this thread for more information and follow the link in post #2 in the thread to a remedy.

[http://ubuntuforums.org/showthread.php?t=2270994](http://ubuntuforums.org/showthread.php?t=2270994)

---

### Post by kerry_s on 2015-05-29
> **Dennis N said:**
> With the 10 min time you mention, you probably suffer from the DPMS problem. See this thread for more information and follow the link in post #2 in the thread to a remedy.

[http://ubuntuforums.org/showthread.php?t=2270994](http://ubuntuforums.org/showthread.php?t=2270994)

i see it's a 14.04 problem.
i would just set "xset -dpms" in startup to disable it.

---

### Post by QDR06VV9 on 2015-05-29
> **amjjawad said:**
> [ATTACH=CONFIG]262298[/ATTACH]

Thank you for replying :)

My apology, I should have mentioned that I have done that already but nothing has changed.
That was the first thing I have done after changing:

[ATTACH=CONFIG]262299[/ATTACH]

and this too:

[ATTACH=CONFIG]262300[/ATTACH]


So, any other idea?!

Thank you :)


I have not had this problem on mate but gnome it was very annoying but this  
Should do the trick [http://www.webupd8.org/2015/01/caffeine-app-gets-its-indicator-back.html](http://www.webupd8.org/2015/01/caffeine-app-gets-its-indicator-back.html) 
Switch's on and off at a click
Regards

---

### Post by Dennis N on 2015-05-29
The MATE screensaver in 14.04 lacks the power to stop DPMS from acting no matter how you set it. Only Xscreensaver has the ability to do that. So if you want a screensaver and a DPMS blocker in one, you need Xscreensaver - and you get a collection of excellent screensavers to use as well.

---

### Post by amjjawad on 2015-05-30
Hi and thanks for your reply :)

> **kerry_s said:**
> set that screen saver to blank screen.
That did not solve the issue at all. I have done that as the first try but it failed.

> also i'm using 15.04, not sure if that matters.

Yes, sometimes it does matter.

> in your terminal check " xset q "
screen saver should be 0
&
dpms should be 0
Here is mine:
```
xset qKeyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
Colors:
  default colormap:  0x22    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On



```

> if there not all 0 you can set them in startup, i've done that in the past when i had those kind of issues.
I will try now to change the timeout of the screen saver. I fail to understand why it is 600 (I'd assume 10 mins) while I have changed that - as I attached the 2 screenshots previously - and via GUI.

Let's see what will happen .. will try to figure out what to do now ... will report back :)

---

### Post by amjjawad on 2015-05-30
> **Dennis N said:**
> With the 10 min time you mention, you probably suffer from the DPMS problem. See this thread for more information and follow the link in post #2 in the thread to a remedy.

[http://ubuntuforums.org/showthread.php?t=2270994](http://ubuntuforums.org/showthread.php?t=2270994)

Hi and thanks for posting :)

Long time no see :) I hope you're fine and doing well!

I am sorry if this is harsh but the link you provided is directing me to another link which is directing to yet another link which is yet another link/thread and to be honest, it is confusing ...

---

### Post by kerry_s on 2015-05-30
for screen saver:
xset s 0 0

add to startup

---

### Post by amjjawad on 2015-05-30
I found this:
[https://techotom.wordpress.com/2012/08/15/removing-10-minute-screen-timeout-for-ubuntu-server/](https://techotom.wordpress.com/2012/08/15/removing-10-minute-screen-timeout-for-ubuntu-server/)

I did the steps but after a reboot, all back to the same.

Need to figure out how to save the changes permanently.

---

### Post by amjjawad on 2015-06-18
Not really a solution but this is what I did.

I installed [**ToriOS**]("http://torios.net/") and I asked our main developer to disable the option by setting:

```
xset s 0 0
```

```
xset dpms 0 0 0
```


So, ToriOS by default, will never go to that status any more. It can be enabled via the power manager.

I will mark this thread as solved :)

Thank you!

---

