---
title: "Touchpad left-click doesn't work in Ubuntu 20.04"
date: 2020-05-31
forum: General Help
---

### Post by bailey919 on 2020-05-31
Hi I'm not new to Ubuntu but please assume i am because my knowledge is extremely limited and most technical terms and jargon will go straight over my head.

I am running Ubuntu 20.04 only on a HP Pavilion dv3-2050ea laptop and i have been having problems with the touchpad. My touchpad looks like this....

[IMG]https://ksassets.timeincuk.net/wp/uploads/sites/54/2009/06/11154-img0537s-1.jpg[/IMG]

The right-click works absoloutely fine, but the left one responds very rarely, if at all. I think I have tried everything I can based on my limited knowledge e.g
- change primary button (sometimes works sometimes doesnt)
- go ino 'tweaks' and change things in there.

yesterday in 'tweaks' under "Mouse Click Emulation" it was on 'AREA'. I changed it to 'DISABLED (don't use mouse click emulation)' and both touchpad mouse buttons worked okay instantly for a few hours but then the left one stopped working again. I tried to set it back to area and then disabled but it didn't work.

I know you may suggest it could be the hardware but i am not technical enough to even check this and it's a secondary laptop so i wouldn't want to send it off anywhere as its not worth it but i would like to try and rescue it if possible. My biggest frustration is that i can only right-click...so on the desktop it comes up with

New folder
Paste
Show desktop in files 
Etc etc when i right-click.

If it was the hardware and the physical left button was broke i could probably live with that as long as I could use the right-one as the primary button and could just get away with copy and pasting with keyboard commands, but its the fact it doesnt even let me do that.

I don't currently have a physical mouse to test it with although I am probably going to try and get a cheap one soon.

Any suggestions? all help would be massively appreciated. Thanks

EDIT: I just randomly decided to try pressing ctrl, alt & f1 as i've seen this suggested elsewhere and now both touchpad buttons seem to be working fine. however i know this won't last very long

---

### Post by dino99 on 2020-05-31
Even if you does not tell us which touchpad make it is, i suppose it should work via xserver-xorg-input-synaptics. 
To get some hints, glance at 'journalctl -b' output into a terminal, and pay attention to the red lines (errors) and yellow ones (warnings, not fatal)

---

### Post by bailey919 on 2020-05-31
> **dino99 said:**
> To get some hints, glance at 'journalctl -b' output into a terminal, and pay attention to the red lines (errors) and yellow ones (warnings, not fatal)

Thankyou for your reply. I did this and didn't get any red or yellow lines was just normal text. I will try and copy and paste it onto here but its difficult on the "Ubuntu laptop" (i am typing this elsewhere)

And yes even though ctrl-alt-f1 did temporarily make both touchpad buttons work i think it lasted about an hour before the left one stopped again. And when I tried to repeat the same thing it had no effect.

---

