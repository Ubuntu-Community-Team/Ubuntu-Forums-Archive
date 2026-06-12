---
title: "Problems with snd_via82xx module based cards"
date: 2004-10-29
forum: General Help
---

### Post by shufla on 2004-10-29
Hello,

[I know, that was on forum, but I haven't found right solution.]

Well, there's little, hm, funny problem with that module. Lets se:```
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
```. That card is associated with module snd_via82xx. Great. Now little story:

I've installed Warty on my home computer with that card. On *ANY* modern Linux there is problem with alsa with that module [bi-boot with SuSe 9.1]. modinfo snd_via82xx says:```
parm:           dxs_support:Support for DXS channels (0 = auto, 1 = enable, 2 = disable, 3 = 48k only, 4 = no VRA)
```. I'd love to put option dxs_support=2. But where in /etc/modutils.d?

By the way, right solution shall be in wiki or any quick accessible media. In my opinion that would be bug...

Best regards,
Lukasz Nowak

Edit: Well, I've got solution for that card, I've put options snd_via82xx dxs_support=2 into /etc/modprobe.d/aliases. I belive that should be default option - shall I report this as feature/bug?

---

### Post by MaZiNgA on 2004-11-11
:shock:  Same problem here! I'll try your workaround.

---

### Post by Julius on 2004-11-11
Same card here. It wasn't working properly (eternal  loops :P). My solution: change the IRQ in BIOS :P

---

