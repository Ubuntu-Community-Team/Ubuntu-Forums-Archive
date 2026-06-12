---
title: "Band in a Box 2008 with Ubuntu?"
date: 2008-06-01
forum: General Help
---

### Post by Ian Drummond on 2008-06-01
I am really getting into my new Ubuntu Hardy Heron software but wondered if any music lovers amongst you could give me some advice? I heavily use Band in a Box 2008 on the XP side of my machine and have tried to install it, through the wine emulator so I can use it in Ubuntu. I could then, more or less, abandon the XP side on a 90% basic. Something I would very much like to do. Unfortunately BB 2008 is not "coming up" when I click on the wine, programs, band in a box icon. I have no idea why because it was installed through the wine emulator. I hope someone might be able to help?

Thanks in anticipation,

Ian.

---

### Post by canopy on 2008-11-20
Hello, 

recently I succeeded to run Band in a Box under wine with timidity as Midi-Player. Most helpful I found the following instructions:

[http://bria.nwood.org/node/244](http://bria.nwood.org/node/244)

Although following these instructions I had problems with the wine midi mapper. The sound was very choppy. For me the solution was the following:

1) Find out the ports of Midi Through and TiMidity by     "pmidi -l"

2) Connect the two ports using the ALSA sequencer connection manager: "aconnect <midi through port> <timidity port>"
    (For me it was  "aconnect 14:0 128:0")

3) Select "Midi Through" in the Midi Output Driver of Band in a Box. 

Hope this works for you also!
Best regards
Johannes

---

