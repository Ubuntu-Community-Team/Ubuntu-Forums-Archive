---
title: "[SOLVED] folder and window plroblems"
date: 2008-02-16
forum: General Help
---

### Post by faineant7698 on 2008-02-16
Hi there :) been using ubuntu for a while now, and it has been going good thus far.  That was until I had gone into my home folder and realized that I am now missing the usual 3 buttons in the right hand corner (minimize, unmaximize/maximize, and close window).  This in itself just a minor anoyance, but I also realised that both the bottom and top panels go missing as well.  As well as any programs programs and certain windows especialy ones that deal with system administration become hidden beneath the folder windows.  If that wasn't bad enough when I am navigating through the home folder or file system the computer will just randomly lock up or hang allowing the mouse curser to still move but unable to click on anything or even restart the system forcing a hard reset via power button on front of machine. 

Any thoughts or comments on this matter would be greatly apreciated.  thank you

---

### Post by randy78 on 2008-02-16
> **faineant7698 said:**
> Hi there :) been using ubuntu for a while now, and it has been going good thus far.  That was until I had gone into my home folder and realized that I am now missing the usual 3 buttons in the right hand corner (minimize, unmaximize/maximize, and close window).  This in itself just a minor anoyance, but I also realised that both the bottom and top panels go missing as well.  As well as any programs programs and certain windows especialy ones that deal with system administration become hidden beneath the folder windows.  If that wasn't bad enough when I am navigating through the home folder or file system the computer will just randomly lock up or hang allowing the mouse curser to still move but unable to click on anything or even restart the system forcing a hard reset via power button on front of machine. 

Any thoughts or comments on this matter would be greatly apreciated.  thank you

Metacity is crashing...

Try this in a terminal:
metacity --replace &

---

### Post by faineant7698 on 2008-02-16
O.K. I tried that and then got this message back:

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

not real sure what this means or how to fix it.  any further help would be great TY.:confused:

The problems I was having with the folder seem to be corrected now though

---

### Post by randy78 on 2008-02-16
> **faineant7698 said:**
> O.K. I tried that and then got this message back:

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

not real sure what this means or how to fix it.  any further help would be great TY.:confused:

The problems I was having with the folder seem to be corrected now though

Are you using an ATI graphics card?

---

### Post by faineant7698 on 2008-02-16
> **randy78 said:**
> Are you using an ATI graphics card?

No I just have the onboard graphics that came with the system an intel graphics media accelerator 950.

---

### Post by randy78 on 2008-02-16
Try this in a terminal:

sudo dpkg-reconfigure xserver-xorg

---

### Post by faineant7698 on 2008-02-17
> **randy78 said:**
> Try this in a terminal:

sudo dpkg-reconfigure xserver-xorg

Ty it looks like everythings back to normal now, just wonder what started the problem.  Been using 7.10 now for few months now and have been having odd little quirks like this popping up from time to time. Anyway if it happens again in the future at least i'll know what to do now.  thanx for all the help.:)

---

### Post by randy78 on 2008-02-17
No problem...

Remember to mark your post as solved so others can use the info that helped you

Use the THREAD TOOLS button near the top:guitar:

---

