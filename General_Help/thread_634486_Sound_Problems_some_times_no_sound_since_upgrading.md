---
title: "Sound Problems: some times no sound since upgrading to Feisty"
date: 2007-12-07
forum: General Help
---

### Post by loopyloopy on 2007-12-07
Hi,

i've been a long time user of Dapper and had no issues with sound on this machine.

recently i upgraded to Feisty and have started having this problem of randomly getting sound or no sound at all with each boot of the machine/os.

i am using an SBLive! Value soundcard for my stereo speakers.  the problem doesnt seem to discriminate whether i use the onboard or sound card sound, i either get sound or none at all.

I have noticed that i can restore sound if i reboot using a different kernel, but then if i reboot using that same kernel i lose sound again.

eg i would boot with 2.6.20-16-386, i would get no sound.
if i reboot with the same kernel, no sound.

if i reboot with 2.6.20-16-generic i would get sound.
if i then reboot with 2.6.20-16-generic i would lose sound,
so i would then reboot with 2.6.20-16-386 and sound would be restored.

it seems something is getting toggled depending on how a reboot was done. no amount of fiddling with the Alsa mixer has made any difference.

I would appreciate any help here.

cat /proc/asound/cards
0 [V8237 ]: VIA8237 - VIA 8237
VIA 8237 with AD1888 at 0x1000, irq 19
1 [Live ]: EMU10K1 - SBLive! Value [CT4780]
SBLive! Value [CT4780] (rev.6, serial:0x80221102) at 0xd400, irq 20

---

### Post by kjoker on 2007-12-11
experiencing the same problem here. i just found out about your post after posting my problem. i switched back using 2.6-20-15 instead of 2.6-20-16.  I got sound
using sblive as well.  i went through all of the possible solution on the "no sound" category but nothing fixed mine. 

Actually your post helped me out by switching back to previous kernel.
i don't know why there wouldn't be any sound with the latest kernel. i'm stumped

---

### Post by bayvista on 2007-12-22
Also having same problem. Tried to install snd-sb8 ALSA drivers using "Sound Troubleshooting" from this Forum. Would appreciate any help on how to undo the changes and return to 2.6.20.16.

David

---

