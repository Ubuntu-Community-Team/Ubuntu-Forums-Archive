---
title: "Calibration problem with Genius 4x5 tablet"
date: 2006-09-27
forum: General Help
---

### Post by v-v on 2006-09-27
Hello,

I have a Genius 4x5 tablet (Tablet WP5540U)
I was following the how-to [here]("https://help.ubuntu.com/community/TabletSetupWizardpen")

The problem is that the pointer is alway in the top-left corner.
I tried experementig with the values but with no luck.

Has anybody an Idea where can be the problem?
In case you have the same or a simmilar tablet working can you paste me your values?

Thanks :)

```
/wizardpen-calibrate /dev/Tablet
Please, press the stilus at ANY
corner of your desired working area: ok, got 741,32745

Please, press the stilus at OPPOSITE
corner of your desired working area: ok, got 32739,1289

According to your input you may put following
lines into your XF86Config file:

        Driver          "wizardpen"
        Option          "Device"        "/dev/Tablet"
        Option          "TopX"          "741"
        Option          "TopY"          "1289"
        Option          "BottomX"       "32739"
        Option          "BottomY"       "32745"
        Option          "MaxX"          "32739"
        Option          "MaxY"          "32745"
```

---

### Post by ashyanbhog on 2006-10-06
Hi, I am also just got my tablet working,

there seems to be a solution for your problem, 

from [http://www.stud.fit.vutbr.cz/~xhorak28/index.php.iso-8859-1?page=WizardPen_Driver_FAQ](http://www.stud.fit.vutbr.cz/~xhorak28/index.php.iso-8859-1?page=WizardPen_Driver_FAQ) 

Cursor is jumping into Upper-Right corner:
Make sure your XF86Config? (or xorg.conf) does not contain /dev/input/mice (mice is driver which unites all input devices into one file). If it does, replace it by proper /dev/input/mouseX.
Also read README in wizardpen driver version >= 0.0.3.

hope that helps :)

---

