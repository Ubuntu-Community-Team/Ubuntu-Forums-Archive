---
title: "No audio after installing Kubuntu 18.04 LTS."
date: 2019-01-17
forum: General Help
---

### Post by marlonmin on 2019-01-17
[COLOR=#242729][FONT=Arial]I installed the Kubuntu 18.04 LTS stable version on my desktop. But I lost sound. On the task bar my audio shows that HDMI DisplayPort 3 (HDA Nvidia Digital Stereo).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Is there a way to fix the issue? Very annoying. My previous 16.04 works well with sound.


[/FONT][/COLOR]

---

### Post by oldrocker99 on 2019-01-17
Try this:```
alsamixer
```

You may have a channel muted, which happened to me Sunday when I was doing a radio show. Alsamixer showed that the main output channel had **somehow** been muted. I unmuted it and the sound came right back. How, it was muted during a show, I have no idea.

---

### Post by SeijiSensei on 2019-01-18
Have you selected the correct device in the audio section of System Settings?

I've also had muting issues from time to time. You should be able to check that using the audio widget in the panel.

---

### Post by marlonmin on 2019-01-18
It works now. Thanks.

---

