---
title: "sound suddenly stopped working"
date: 2013-10-16
forum: General Help
---

### Post by bricro on 2013-10-16
Hello, i have just installed lubuntu lxle on my wife's compaq cq60 laptop mainly for her facebook and music. After installing i loaded all her music and everything worked a treat. I then updated and there is no sound at all not from any music player movie player or you tube. I checked the volume settings and they are all turned up. On the same laptop i have mint 13 installed and it works fine (i thought i maybe broke something).  I then booted into the pre updated kernel of lubuntu when the sound worked and it doesn't work in there either now. any suggestions and if it involves fitting drivers could you explain what to do please thank you for your time ,Brian.

---

### Post by Dennis N on 2013-10-16
Check settings in alsamixer as well as the panel's volume control. In particular, PCM. Access alsamixer from the terminal with 'alsamixer'. PCM may be set too low. (The other setting, Master, mirrors the Volume control on the panel).

---

### Post by ronniew on 2013-10-16
Something is muted, make sure there in no checkmark under the volume slider, also you can find the alsamixer in the control center.

---

### Post by bricro on 2013-10-17
> **Dennis N said:**
> Check settings in alsamixer as well as the panel's volume control. In particular, PCM. Access alsamixer from the terminal with 'alsamixer'. PCM may be set too low. (The other setting, Master, mirrors the Volume control on the panel).

checked the alsamixer settings PCM. master etc. all turned up also checked volume on music player and you tube which are also at 100% Another option i tried was in alsamixer f6 gives a default setting and the name of the sound card (nvidia....) and tried both settings. Just to recap the music plays fine on mint on the same computer and it played fine when i first installed lubuntu. It was after i updated it dissapeared and even using previous kernel still nothing. As i have limited knowledge of the workings i don't know what else to do except reinstall try it then update and see if it happens again but i REALLY don't want to do that.Here's hoping some of you clever fellows can help thanks Brian

---

### Post by Dennis N on 2013-10-17
I didn't catch the mention on LXLE, which a quick check tells me is a distro based on Lubuntu 12.04. It may have pulse audio installed as an additional package, which Lubuntu does not. If so, one more sound setting device would be the Pulse Audio volume control, which is probably under Sound and Video. I would check into that if you haven't already.

LXLE has a forum you might want to visit if you haven't. Maybe something/someone there may help.

[http://sourceforge.net/p/lxle/discussion/](http://sourceforge.net/p/lxle/discussion/)

---

### Post by pqwoerituytrueiwoq on 2013-10-17
using 12.04, 12.10, or 13.04?
i have access to a cq60-215dx
i think the micophone is dead on it

---

### Post by bricro on 2013-10-19
> **Dennis N said:**
> I didn't catch the mention on LXLE, which a quick check tells me is a distro based on Lubuntu 12.04. It may have pulse audio installed as an additional package, which Lubuntu does not. If so, one more sound setting device would be the Pulse Audio volume control, which is probably under Sound and Video. I would check into that if you haven't already.

LXLE has a forum you might want to visit if you haven't. Maybe something/someone there may help.

[http://sourceforge.net/p/lxle/discussion/](http://sourceforge.net/p/lxle/discussion/)

a thousand thank you's it really was as simple as checking the pulse audio settings which must have muted somehow when i updated. I cannot express how gratefull i am to be able to use my fast becoming favorite flavor.:p

---

### Post by Dennis N on 2013-10-19
Success is a wonderful feeling! Glad to learn I was helpful.

---

