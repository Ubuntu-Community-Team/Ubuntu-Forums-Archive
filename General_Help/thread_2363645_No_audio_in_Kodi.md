---
title: "No audio in Kodi"
date: 2017-06-12
forum: General Help
---

### Post by cable_guy on 2017-06-12
hi all,

I have set up xubuntu as a minimal install of ubuntu to boot straight to Kodi.

It all works great, except I have no audio output from my Nvidia HDMI graphics card from Kodi.

I have the correct Nvidia drivers, any ideas please?

thanks in advance!

---

### Post by Tadaen_Sylvermane on 2017-06-12
Did you set kodi sound to output to hdmi?

---

### Post by lisati on 2017-06-13
*Thread moved to **General Help**.*

---

### Post by cable_guy on 2017-06-13
yep tried HDMI and default. #-o

---

### Post by Tadaen_Sylvermane on 2017-06-13
Only other possibility i can think of... is user in audio group? Also kodi has its own volume setting. Make sure it isnt muted or down all the way.

---

### Post by cable_guy on 2017-06-18
> **Tadaen_Sylvermane said:**
> Only other possibility i can think of... is user in audio group? Also kodi has its own volume setting. Make sure it isnt muted or down all the way.
thanks for the tip, I checked and indeed my user for Kodi was not in the audio group.  Added him, and still no sound :( It's doing my head in as i've configured the rest of the apps on the server just the way I want them.  I wish Kodi team would bring back Kodibuntu :(  No idea where to turn next for an auto-login straight to Kodi system

---

### Post by #&amp;thj^% on 2017-06-18
> **cable_guy said:**
>  No idea where to turn next for an auto-login straight to Kodi system

I had to vary some of what was covered here. **(I did not add the PPA)**
[https://askubuntu.com/questions/596839/autostart-kodi-on-vivid](https://askubuntu.com/questions/596839/autostart-kodi-on-vivid)

This Kodi link is for upstart && systemd:

[http://kodi.wiki/view/HOW-TO:Autostart_Kodi_for_Linux](http://kodi.wiki/view/HOW-TO:Autostart_Kodi_for_Linux)

No "Offense" meant but please read carefully. :)

---

### Post by cable_guy on 2017-07-08
> **1fallen said:**
> I had to vary some of what was covered here. **(I did not add the PPA)**
[https://askubuntu.com/questions/596839/autostart-kodi-on-vivid](https://askubuntu.com/questions/596839/autostart-kodi-on-vivid)

This Kodi link is for upstart && systemd:

[http://kodi.wiki/view/HOW-TO:Autostart_Kodi_for_Linux](http://kodi.wiki/view/HOW-TO:Autostart_Kodi_for_Linux)

No "Offense" meant but please read carefully. :)

> **Tadaen_Sylvermane said:**
> Only other possibility i can think of... is user in audio group? Also kodi has its own volume setting. Make sure it isnt muted or down all the way.

guys I have to fess up here. Turns out the HDMI cable wasn't fully seated :oops:

I know it's extremely embarrassing but I felt I needed to give the guys who've helped me full closure on this.

---

### Post by #&amp;thj^% on 2017-07-08
> **cable_guy said:**
> guys I have to fess up here. [B][U]Turns out the HDMI cable wasn't fully seated :oops:
[/U][/B]
I know it's extremely embarrassing but I felt I needed to give the guys who've helped me full closure on this.

hehe It happens to the best of us.:D
Glad you got it working though.

---

