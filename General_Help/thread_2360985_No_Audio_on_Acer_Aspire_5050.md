---
title: "No Audio on Acer Aspire 5050"
date: 2017-05-10
forum: General Help
---

### Post by Ryukenden on 2017-05-10
I have no speaker and headphone audio on my laptop. It worked up to xubuntu 15.10

I've ran ./alsa-info.sh --stdout |grep "ixer name" and i get:
  Mixer name	: 'Conexant Generic HDMI'

and

aplay -l
**** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: SB [HDA ATI SB], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
placa 0: SB [HDA ATI SB], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


I think it's because the audio mixer may be set to HDMI.
How do i get the speakers and headphones working again?

---

