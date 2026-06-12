---
title: "middle mouse button remapped?"
date: 2015-02-24
forum: General Help
---

### Post by elson2 on 2015-02-24
I have a Ubuntu 12.04 system on a Dell desktop, with a 3-button trackball.  I use the middle mouse button to paste.
Suddenly, it doesn't work anymore.  After checking with xev, I can see the outer mouse buttons generate
ButtonPress and ButtonRelease events.  But, the middle button generates a LeaveNotify and EnterNotify
event instead.  (I checked on another system where the paste works, and all 3 buttons create
ButtonPress events.)  Anybody know where the buttons are mapped to these X events?

Thanks,

Jon

---

### Post by papibe on 2015-02-24
Hi elson2.

I can't answer all your questions, but may be I can help you to remap your buttons.

Somehow, from 12.04 to 14.04, the mapping of my mouse ([Evoluent]("http://www.amazon.com/gp/product/B00427TAIK/ref=pd_lpo_sbs_dp_ss_2?pf_rd_p=1944687642&pf_rd_s=lpo-top-stripe-1&pf_rd_t=201&pf_rd_i=B006P2594Y&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=1NS5X18DSJV09EKQEFB0")) changed.

This is the script I use to remap it back how it used to:
```
#!/bin/bash
device=$(xinput list | grep -i evoluent | awk '{print $8}' | sed 's/^id=//')

xinput set-button-map "$device" 1 2 3 4 5 6 7 2

```
You have to change it to your specs, in order to make it work. Studying the command 'xinput' is the key to re mapping the buttons.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by elson2 on 2015-02-24
Thanks, but the remapping is 1 2 3 4 5 6 ..., so nothing in the button sequence got changed.  I am now starting to think the mouse may
actually be bad, maybe it has started sending invalid messages when the middle button is pressed.  I will try another tomorrow.

Jon

---

### Post by Jon_Elson on 2015-02-25
OK, I tried with a different mouse, same problem.  Middle button registers as a LeaveNotify / EnterNotify
instead of a ButtonPress / ButtonRelease sequence.  Either there is some remapping of the
buttons or possibly the driver has identified the mouse type as the wrong protocol (MS vs. Mouse
Systems or something like that.)  These are both PS/2 trackballs.  One is a Logitech, the other is iOne.

Any ideas where to look?

Thanks,

Jon

---

### Post by Jon_Elson on 2015-02-25
Much more fooling around, I now discover that when I hold the keyboard shift key down, the middle mouse button now gives only the correct ButtonPress and ButtonRelease events, and the paste fuction again works.
So, in the past, you did NOT need to press shift to get this function.  Anybody know how to make the middle mouse button give ButtonPress for button 2 without holding keyboard shift?

Thanks,

Jon

---

### Post by Jon_Elson on 2015-02-25
ARRGH!  Linux is getting too complex for mere mortals!

OK, so I removed the .xbindkeysrc file and rebooted, and the problem is fixed.  When I installed xbindkeys and created the new .xbindkeys file, it
must have grabbed the key binding I was trying to eradicate and entered it into the file.  However, m:0x0 + b:2 seems like it should be
mapping the middle button with NO modifiers pressed.

Anyway, it only took me TWO DAYS to fix this??!!??

Jon

---

