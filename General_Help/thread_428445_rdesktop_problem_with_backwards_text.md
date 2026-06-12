---
title: "rdesktop problem with backwards text"
date: 2007-04-30
forum: General Help
---

### Post by eli0001 on 2007-04-30
I have just upgraded to feisty, and one problem followed me from edgy. In rdesktop connecting to Win2k3 Server I get som text in 9 pt fonts with certain letters(b,f,l...) facing the wrong way. I can change the font size and it goes away. Its not my dyslexia kicking in. Any workaround? I found answers for just about every other problem, I hope I'm not the only one with this one. Tried upgrading with package from getdeb.net, same issue. This is useable but quite annoying. Thanks in advance.

Eli

---

### Post by eli0001 on 2007-04-30
Minor update, if I set the res really low, like 250x250 then it goes away. It is the most noticeable on the start button which has backwards t's. Computer is a HP laptop with the Ati 340M chip, P4 2.4 GHz, 512 MB, weighs 8 lbs, blows like a space heater, and sounds like a turbine. Please tell me its just my hardware so I will have another reason to replace it. Thanks again.

Eli

---

### Post by unicell on 2008-01-10
I just run into the same problem...

Please add following line to "Device" section, hope it helps.

Option           "XAANoOffscreenPixmaps" "true"

---

