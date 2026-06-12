---
title: "Lubuntu 14.04 Unable to disable tap to click"
date: 2015-07-25
forum: General Help
---

### Post by Vidorin on 2015-07-25
Hello! I am trying to disable tap to click in Lubuntu 14.04.  I downloaded the pointing devices add which lets me disable tap to click.  However, it does not stick once the computer is restarted and disabling tap to click has to be enabled each time.   Is there a way to permanently disable tap to click?  Thank you in advance.

---

### Post by sudodus on 2015-07-25
You can add the command ***synclient touchpadoff=2*** into the file

```
$HOME/.config/lxsession/Lubuntu/autostart
```

for example with the following command line

```
echo 'synclient touchpadoff=2' >> $HOME/.config/lxsession/Lubuntu/autostart
```

Then it will be run every time you log in to Lubuntu.

Read more in the manual ```
man synaptics
```

```
       Option "TouchpadOff" "integer"
              Switch off the touchpad.  Valid values are:

              0   Touchpad is enabled
              1   Touchpad is switched off (physical clicks still work)
              2   Only tapping and scrolling is switched off
              When the touchpad is switched off, button events caused by  a  physical  button  press  are
              still  interpreted. On a ClickPad, this includes software-emulated middle and right buttons
              as defined by the SoftButtonAreas setting.

```

---

### Post by Vidorin on 2015-07-26
Thank you very much that code worked and fixed the problem.  Time to mark this one as solved.  :D :guitar:

---

