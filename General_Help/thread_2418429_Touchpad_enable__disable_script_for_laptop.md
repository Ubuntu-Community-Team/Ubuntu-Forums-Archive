---
title: "Touchpad enable / disable script for laptop"
date: 2019-05-06
forum: General Help
---

### Post by rdh61 on 2019-05-06
Hi,

I have a script that lets me disable and re-enable my laptop touchpad.

This is the script:

```
#!/bin/sh
if xinput list-props 13 | grep "Device Enabled (143):.*1" >/dev/null
then
  xinput disable 13 
  notify-send -u low -i mouse "Touchpad disabled"
else
  xinput enable 13
  notify-send -u low -i mouse "Touchpad enabled"
fi

```

I have saved the text file as "tt.sh" in /usr/bin.

Thus, entering "tt.sh" in the command line I can toggle between touchpad enabled / disabled.

Trouble is, I use my laptop in different places with different mice. Someimes my touchpad ID is listed as "12" and sometimes as "13". So the script doesn't always work unless I change it, which is cumbersome and somehow defeats the point.

Is there a way round this?

Many thanks.

---

### Post by Holger_Gehrke on 2019-05-06
Sure, use the Name instead of the ID.
On my system xinput --list gives me:
```

...
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=13    [slave  pointer  (2)]
...

```
so to switch it off, I'd do
```

xinput disable "ETPS/2 Elantech Touchpad"

```


Holger

---

### Post by rdh61 on 2019-05-06
Thank you!

---

