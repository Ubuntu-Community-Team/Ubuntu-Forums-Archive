---
title: "Attaching hotkey to script with acpi doesn't work"
date: 2013-10-08
forum: General Help
---

### Post by pawel.ad on 2013-10-08
Hi!
I own ThinkPad x220 with elementary os 0.2 (based on Ubuntu 12.04) and generally everthing works out of the box but the Fn + Backspace combination doesn't do anything (I think it should do maximization, witch is kind of useless...) and I wanted to assign it to the script that turns off the display.

So, based on [this]("https://help.ubuntu.com/community/LaptopSpecialKeys") I created a file /etc/acpi/events/display-off ```

vent=ibm/hotkey HKEY 00000080 00001014
action=/etc/acpi/display-off.sh

```

Base on [this]("http://askubuntu.com/questions/248972/how-can-i-disable-backlight-when-i-lock-the-screen"), my /etc/acpi/display-off.sh
```

#!/bin/sh
sleep 0.5
xset dpms force off

```

acpi_listen output:
```

ibm/hotkey HKEY 00000080 00001014

```

I made the sh file executable, doing "sudo sh /etc/acpi/display-off.sh" works, but the hotkey doesn't.

I run out of ideas - do you have any? Or mayby I'm missing something basic?

Thanks in advance.

Cheers
Pawe&#322;

---

### Post by Toz on 2013-10-08
xset requires an active X session to work. The acpi daemon doesn't run in your user profile and therefore doesn't have access to your X session, so xset won't work.

You could try to export your display:
```
#!/bin/sh
export DISPLAY=0:0
sleep 0.5
xset dpms force off
```
...but you might also need to export your Xauthority for this to work. _However_, this is not how acpi is intended to work.

As an alternative, why don't you just set up a keyboard shortcut to run the script?

---

### Post by pawel.ad on 2013-10-08
Thanks for the anwser. Exporting unfortunately doesn't work.
Do you have any other ideas?

Is there mayby any other way to turn off the display without xset?

I just wanted to get it done with the Fn button, but yeah, I supose I could do that :-)

Thanks

---

### Post by Toz on 2013-10-08
Try creating a [keyboard shortcut]("http://elementaryos.org/answers/keyboard-shortcuts") to run that script. Assign it to Fn+Backspace.

---

### Post by pawel.ad on 2013-10-08
Yeah, I tried that at the very beginning but it doesn't recognize Fn key's. That's why I came out with the wole acpi idea.
For now I did that for Ctr+Backspace, but if I could assign it to Fn it would be cool :)

---

### Post by Toz on 2013-10-08
Does:
```
vbetool dpms off
```
...work in the acpi script (instead of xset)? You may have to install vbetool if its not installed. I don't believe it requires X.

---

### Post by pawel.ad on 2013-10-08
After that I couldn't turn the screen on and had to restart the computer ;)

OK, never mind - I'm all good with the Ctr+spacebar combination.

Thanks for the help though and for the explanation why the acpi didn't work.

Cheers!

---

