---
title: "cannot get into bios"
date: 2008-04-15
forum: General Help
---

### Post by Lexus Dominus on 2008-04-15
having a weird problem.. 
every time i restart my computer, my keyboard shuts down & wont let me into bios or use the menu to choose the OS. gutsy boots up & the keyboard starts working. anyone got any ideas? thanks

---

### Post by kutjara on 2008-04-15
> **Lexus Dominus said:**
> having a weird problem.. 
every time i restart my computer, my keyboard shuts down & wont let me into bios or use the menu to choose the OS. gutsy boots up & the keyboard starts working. anyone got any ideas? thanks

Are you using a USB keyboard? It may be that your BIOS doesn't enable USB, in which case you'll need to invest in either a PS/2 keyboard or buy one of those little USB to PS/2 dongle thingies. A dongle costs only a couple of dollars and, since you'll only be using it for that tiny part of the bootup phase, it's probably the most cost-effective way to go.

---

### Post by Lexus Dominus on 2008-04-15
nope ive got a ps/2 keyboard. the mouse shuts down too; the light switches off - that is a usb connection.

---

### Post by kutjara on 2008-04-15
> **Lexus Dominus said:**
> nope ive got a ps/2 keyboard. the mouse shuts down too; the light switches off - that is a usb connection.

Hmm, that's just plain weird. PS/2 should be recognized by the hardware the instant you boot up. Is it an old PC? I ask because maybe your CMOS settings have got messed up somehow, so the hardware isn't recognized until Ubuntu goes and finds it.

---

### Post by Shazaam on 2008-04-15
> **Lexus Dominus said:**
> nope ive got a ps/2 keyboard. the mouse shuts down too; the light switches off - that is a usb connection.

Turn off your pc. Disconnect the usb keyboard. Connect up a spare ps/2 keyboard to your ps/2 port. Can you access the bios after this?

---

### Post by Lexus Dominus on 2008-04-15
my sys specs:
gigabyte ga-81915g pro motherboard
p4 dual core 3.4ghz
ati radeon x300 128mb
1ghz ddr ram
200gb hd

to be fair my computer took a knock & then messed up. it was working fine before. is there some way i can reset the bios on the board? is it safe? thanks..

---

### Post by elmer_42 on 2008-04-15
I found a way to reset your BIOS [here]("http://wiki.answers.com/Q/How_do_you_reset_the_BIOS"). NOTE: I have not tried this, do it at your own risk. The article is not long by any means, but this is the main part:
> So now you have two options to reset your BIOS:

1. You can take out the battery and then re-install it. or 2. You can toggle the BIOS reset jumper.

Both the ways the BIOS will be reset to the factory settings.

For the second option you may need to refer to the mainboard manual. 

---

