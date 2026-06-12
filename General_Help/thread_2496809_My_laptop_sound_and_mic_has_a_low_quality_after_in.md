---
title: "My laptop sound and mic has a low quality after installing Ubuntu 22.04.4 LTS."
date: 2024-04-13
forum: General Help
---

### Post by paulliano1 on 2024-04-13
I'm new to Linux, and It's been weeks now, I have been trying to fix my  laptop sound, HP ENVY x360 Convertible 15-cp0xxx. The sound is very low in quality with no bass, and the mic  makes noise. I've tried so many solutions I found online but still no  avail. Any idea or suggestion of what to do will be appreciated, thanks

---

### Post by hyperlinxe on 2024-04-13
You can use the package pulseeffects for pulseaudio sound effects, and modulation, like boosting the bass levels,

but initially you are going to want to get a pair of high quality headphones to get good sound quality whatsoever, or

speakers. 

Also, please add the music you are using for testing sound quality please.

---

### Post by ajgreeny on 2024-04-13
Laptop sound is, and always has been notoriously bad, particularly related to bass output. Have you used the same laptop with any other OS, eg, of course, Windows where you think it was much better?

I would agree with the last poster that the only good way to listen on any laptop I have used has been either headphones or external speaker(s).  In my experience, sound has got worse in the most recent very thin laptops where speakers have insufficient space behind them to produce worthwhile sound output.

---

### Post by paulliano1 on 2024-04-13
I have installed pulseaudio but I kept getting same results. I beleive this has something to do with the settings as I am still trying to understand how things work better.

---

### Post by paulliano1 on 2024-04-13
> **ajgreeny said:**
> Laptop sound is, and always has been notoriously bad, particularly related to bass output. Have you used the same laptop with any other OS, eg, of course, Windows where you think it was much better?

I would agree with the last poster that the only good way to listen on any laptop I have used has been either headphones or external speaker(s).  In my experience, sound has got worse in the most recent very thin laptops where speakers have insufficient space behind them to produce worthwhile sound output.

Maybe there is a configuration that could work for this. Any suggestion?

---

### Post by hyperlinxe on 2024-04-13
pulseaudio is already the default on jammy jellyfish I believe, so that would mean, that you can't install it, as it's already installed.

The configuration that solves your problem, is actually using a decent pair of headphones, or speakers, that have some bass even. I got a pair of headphones with high quality sound/bass for 20$ on the internet, and they lasted for about 3 years, then I bought another pair, and now they've lastest about 3 years too.

With the volume controls on your desktop you can go into settings and check over amplification, which will let you turn the volume above 100% to 150%

Other than that, you should try using pulseeffects like I said. You install it like this...

sudo apt install pulseeffects

then you can run the app and play with the hundreds of sound modifying settings it provides....alongside the basic ones like the equalizer.

---

### Post by him610 on 2024-04-13
You may want to investigate and use *alsamixer*

---

