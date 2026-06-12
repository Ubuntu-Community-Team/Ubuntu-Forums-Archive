---
title: "Sound &amp; Application help"
date: 2006-12-29
forum: General Help
---

### Post by klhrevolutionist on 2006-12-29
Hello, I have been able to get sound on edgy via adding a line to /etc/modules "snd-cs4236"
I do hope that is the most appropriate way to do this.

Now I am wanting to use two apps that use sound at same time, xmms & gizmo.
Due to the lack of literate documentation I cannot figure out how to do this so I am hoping somebody might help out.

---

### Post by der_joachim on 2006-12-30
First, make sure that you are using alsa. Since you installed Ubuntu, that is probably very much the case, but I'd double check.
Second: read [this link]("http://alsa.opensrc.org/AlsaSharing") about configuring alsa. Alsa sharing is disabled by default because some old (ancient!) sound cards might break when this were enabled. 
Third: restart alsa with the command```
sudo /etc/init.d/asound restart
```

Good luck.

---

