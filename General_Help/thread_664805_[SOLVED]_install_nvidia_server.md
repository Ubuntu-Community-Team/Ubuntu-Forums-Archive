---
title: "[SOLVED] install nvidia server"
date: 2008-01-11
forum: General Help
---

### Post by timboellis on 2008-01-11
I have just Installed Ubuntu all working fine BUT.....................

I just cannto get the Nvidia drivers working well I think I cannot

Well first of all the Nvidia splash screen does not come up up first logon if this is relevant

Cannot get the Nvida server loaded where I can setup various control with graphics and monitor

I tried a couple of games and they are slow bad you woudl think i was using a 1 meg graphics card

I tried Sabayon all worked like a dream just from the live CD

Please help I really want to stick to Ubuntu the best I have ever tried


I am running a AMB Semptrom 2800 , Nvidia 7300 GT 512m AGP card 24" TFT

---

### Post by #Reistlehr- on 2008-01-11
did you use the following commands to install it?

```

sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig --add-argb-glx-visuals

```

---

