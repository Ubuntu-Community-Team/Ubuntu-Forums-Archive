---
title: "Sound issues"
date: 2007-07-17
forum: General Help
---

### Post by Ziggyz on 2007-07-17
Ok, here it goes. 

I start up teamspeak, then I go to play some music, and I cant hear it. 

I start playing some music, then load teamspeak and I cant talk or hear anyone.

I start eve online, then music and I cant hear the music.

So, I can run more than 1 program at a time that emits sound, but the one I started first is the only one I will be able to hear. What does this mean and how do I fix it (If possible).

---

### Post by Ziggyz on 2007-07-19
Could anyone have any possible answers for this? Was linux designed to only have 1 decive playing sound at a time?

---

### Post by der_joachim on 2007-07-20
I may be able to help you, but there may be major tinkering ahead. Anyhoo, your problem is probably that your alsa is configured by default to use one channel at a time. This is because apparently some older chipsets may not like this setting and it may apparently break them. 

[This link]("http://alsa.opensrc.org/AlsaSharing") points to a guide which gives you a step by step guide to alsa sharing. A word of warning though: there is a reason that alsa sharing was not enabled by default. Please proceed with extreme caution. 

That being said, even my ancient SB128 worked perfectly.

---

### Post by Ziggyz on 2007-07-24
Should I buy a sound card just in case?

---

### Post by longlegs on 2007-07-24
No.

---

