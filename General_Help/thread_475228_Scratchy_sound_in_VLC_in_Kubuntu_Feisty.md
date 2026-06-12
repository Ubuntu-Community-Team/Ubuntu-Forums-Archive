---
title: "Scratchy sound in VLC in Kubuntu Feisty"
date: 2007-06-15
forum: General Help
---

### Post by srunni on 2007-06-15
Hi,

I'm running Kubuntu Feisty with VLC Media Player 0.8.6. I have an issue with scratchy audio in VLC, which doesn't happen in Amarok, Kaffeine, MPlayer, or anything else. I have ALSA 1.0.13, if that helps.

Thanks in advance for the help!!

---

### Post by Bonz on 2007-07-19
I had the exact same problem, and I am very new to Linux so I don't know if this is the right thing to do or not but it worked for me.  In VLC under Audio>Output Modules>ALSA, I changed the ALSA device to my Intel HDA ANALOG input.  Not the digital input.  The scratching isn't there anymore :D Also you might have to refresh the list for it to appear.  Let me know if this works for you too :)

---

### Post by srunni on 2007-07-20
I think it kind of worked - the scratching has decreased, but I still hear a little. Or maybe that's something else. Anyway, thanks for the help. I think the real issue is with my Sigmatel sound card, which isn't supported very well on Linux.

---

### Post by madsravn on 2008-02-24
Thanks a lot. Sure helped me out. I had a LOT of scratching.

---

