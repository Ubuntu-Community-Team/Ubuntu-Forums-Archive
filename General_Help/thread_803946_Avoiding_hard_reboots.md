---
title: "Avoiding hard reboots"
date: 2008-05-22
forum: General Help
---

### Post by Crossroads on 2008-05-22
[QUOTE="ago, in another thread:"]You can avoid hard reboots using [https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a](https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a)[/QUOTE]

ago,
Could you expand on this a bit for a UNIX newbie?

As far as I understand, these key sequences can be used in Ubuntu (or any Linux?) even if my PC has locked up and does not respond to the keyboard or mouse.

TIA

---

### Post by tamoneya on 2008-05-22
i typically see this one: ALT+ SYSRQ + R + S + U + B with an I and an E in it. ALT+ SYSRQ + R + E + I + S + U + B.

---

### Post by ago on 2008-05-24
Correct you run those sequences from Ubuntu even if your screen/keyboard seem locked. I have added more explanations to the wubiguide.

Wor wubi R + S + U + B is recommended over R + E + I + S + U + B

Because E/I kill the existing processes, and hence also ntfs-3g...

---

### Post by Crossroads on 2008-05-24
> **ago said:**
>  For wubi R + S + U + B is recommended 

[SIZE="5"]"[COLOR="Red"]R[/COLOR]eal [COLOR="Red"]S[/COLOR]oft [COLOR="Red"]U[/COLOR]buntu [COLOR="Red"]B[/COLOR]oot"[/SIZE]

[https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a](https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a)

Thanks

---

### Post by nooby on 2008-05-28
But how long time should hold them down. Should one look for any change on computer or screen. 

What does it mean? 
> ALT+ SYSRQ + R + S + U + B (forces a clean reboot even when the keyboard is not responding) 

Do I touch alt for one second and then release it and then touch sysrq for one second and release and then touch r for one second ... 

Or should I hold down alt and then using other hand hold down sysrq and still holding down alt and touching r and still holding down alt and touching s ... 

for how long should one hold down sysrq? 

Nothin did happen at my computer. I need step for step instruction to get it going. 

Please!

---

### Post by ago on 2008-05-28
Keep down ALT+ SYSRQ 
Then press in order R then S then U then B
Nothing happens until you press B, then suddenly the computer reboots

---

### Post by nooby on 2008-05-28
Thanks indeed Ago for your persistent assistance in this forum. Much appreciated so the following is not criticism ok! 

You forgot me is a noob. You don't say for how long I have to old them down 
and for how long to wait between each. They should stop things and such takes time as far as I know. But ok I give it a try. 

What do I write so I get a log to look at if it fails? 

You write that it reastarts but I want to learn how to do a 
clean shut down that don't destroy mbr in grup or whatever the name. 

restart works for me if I do a suspend first. It is the shut down that 
is the important one I need to know how to. 

So could you please give it a new post. Sorry for taking up your time again. 

I write in Ulteo Linux now and that one have not shutdown problem at all. 

Wish Ubuntu to work too cause Ulteo is still in Beta and not all is implemented yet.

---

