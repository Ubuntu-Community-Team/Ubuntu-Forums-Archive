---
title: "Attach correct soundcard to volume multimedia keys"
date: 2006-10-21
forum: General Help
---

### Post by RikBlankestijn on 2006-10-21
Hi,

I asked the same thing probably a year ago and have seen threads about it but found no answer. 

**How can I attach the correct soundcard to the multimedia volume keys?**

I've got two soundcards in my pc, an onboard card and a soundblaster card. I want to have the latter attached to the volume keys. The volume keys are working; I see the volume bar appearing on screen but the volume does not really change so I guess it's attached to the first one. 
Since I've not found an answer to the above yet maybe you can answer the following question which could probably help me. (I've upgraded to Edgy but had the problem in dapper too)

How can I completely ignore (prevent drivers loading) the first soundcard? So that Edgy only sees the soundblaster card?

kind regards,
Rik Blankestijn

---

### Post by RikBlankestijn on 2006-10-21
I managed to ignore the onboard module from loading by adding
[COLOR="SeaGreen"]blacklist snd_intel8x0[/COLOR] to **/etc/modprobe.d/blacklist** now the volume keys work as they should.

---

