---
title: "Brightness Keys on Toshiba Chromebook 2"
date: 2018-09-25
forum: General Help
---

### Post by smiddsy on 2018-09-25
I have recently replaced the ChromeOS operating system on my Toshiba  Chromebook 2 with the latest version of Ubuntu (18.04.1 LTS) and so far  all is well except for the missing functionality of the brightness keys.  On previous versions of Ubuntu (16, I believe) I was able to use a  command to change brightness levels and key-bind those commands to the  brightness keys. Now, however, I have been able to find a command which  affects the screen brightness at all.

Is there anything that I might be able to do to map the brightness keys  alone to their functionality? I am aware that Ubuntu has built in  capacity to change brightness when the key is joined with 'fn', however my keyboard lacks such a key.

Thanks!

---

### Post by TheFu on 2018-09-25
I have one of these and run Ubuntu ... something with openbox on it.
I have 2 scripts to change the brightness.

Brighter:
```
#!/bin/sh

FILE=/sys/class/backlight/intel_backlight/brightness
sudo sh -c "/bin/echo 280 > $FILE "
exit;
```

Dimmer:
```
#!/bin/sh

FILE=/sys/class/backlight/intel_backlight/brightness
sudo sh -c "/bin/echo 120 > $FILE "
exit;
```

How you hook those scripts up to the brighter and lower keys for your DE is different from mine.
BTW, there used to be a program, xbacklight, that handled it nicely, but that stopped working on 16.04 sometime. When I run it today, I get 
```
$ xbacklight -get
No outputs have backlight property

```

---

### Post by smiddsy on 2018-09-26
Yeah ```
$ xbacklight
``` used to be my go to method but seeing as that no longer works I've been a little unsure of where to go. It looks as though your script works on my machine though, which is a promising start! Is there any way we might be able to obtain the value of the current brightness and do some simple arithmetic to subtract values and add values, restoring the increasing and decreasing functionality to the brighten and dimmer keys?

---

### Post by TheFu on 2018-09-26
yes, there is.  Not my itch.

---

