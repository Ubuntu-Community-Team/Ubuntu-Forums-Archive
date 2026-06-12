---
title: "gnome don't recognize audio card."
date: 2016-10-16
forum: General Help
---

### Post by viozzis333 on 2016-10-16
hi i have a asus vivobook e200h with a fresh installation of gnome and the audio doesn't work.

in the audio setting the audio output is "output dummy".

heres the output for some command that i try

```
aplay -l
aplay: device_list:268: nessuna scheda audio trovata...


```

```
lspci -v | grep -A7 -i "audio"
--nothings--

```


i also try to reinstall all alsa package:
```
[COLOR=#000000]sudo apt-get remove --purge[/COLOR][COLOR=#000000] alsa-base[/COLOR]
[COLOR=#000000]sudo apt-get remove --purge[/COLOR][COLOR=#000000] pulseaudio[/COLOR]
[COLOR=#000000]sudo apt-get install alsa-base[/COLOR]
[COLOR=#000000]sudo apt-get install pulseaudio[/COLOR]
[COLOR=#000000]sudo alsa force-reload[/COLOR]

```  

but it dos't work...

thank a lot for the support:D

simone viozzi

---

