---
title: "Night Light 24/7?"
date: 2018-06-25
forum: General Help
---

### Post by gbrandon on 2018-06-25
It's nice that this feature is built in now, but I want to keep it on 24/7.  This is my current compromise:
[ATTACH=CONFIG]280215[/ATTACH]
It seems that without the 1h 1m window of off-time, the feature stops working altogether.  Worse, the off-time seems to actually last a lot longer than specified...

---

### Post by QIII on 2018-06-25
Hello!

As a courtesy to those with slow connections or data limits, please use the attachment functionality provided by the "paperclip" button in the tool bars above the text entry box when using images.

Let others decide if they want to bear the expense of the data transfer by viewing the full-sized image.

Thanks!

What is it specifically that you would like the community to help you with?  Configuration of the utility?  We can't help at all with changing the software.

---

### Post by gbrandon on 2018-06-25
Ah, sure... Is there a way to make it visible without registering, however?

---

### Post by QIII on 2018-06-25
Only registered and logged-in users will be able to view it.

---

### Post by Holger_Gehrke on 2018-06-25
Most displays have the ability to either set the colour balance directly or set a colour temperature. So if you want warmer colours all the time why not deactivate Night Light completely and set the colours through the OSD of the display ?

Holger

---

### Post by gbrandon on 2018-06-26
That sounds rad, but the internet seems to be saying the only way to do that is to install redshift, which I used to use before night light was added.  I could go back to redshift.

---

### Post by Holger_Gehrke on 2018-06-26
May I assume a display integrated into a laptop from your post ? I kind of assumed an external display -- with an OSD and buttons to manipulate it -- in my last post. With a laptop display you can try to use xrandr in a terminal and set gamma per channel:
```

xrandr --output eDP --gamma 1.1:0.9:0.9

```
You can find the value to put after the option '--output' in the output of xrandr without options. The values after --gamma give the gamma values for red, green and blue. Settings you make that way will stay active until you change them or you reboot. To make them persist across reboots, put your xrandr line into a script file that gets started at the beginning of your session (how to do that depends on the desktop environment you're using).

Holger

---

### Post by gbrandon on 2018-06-27
Ah, that would be adjusting the RGB balance to be more red?  Thanks, I will have to try it!

---

