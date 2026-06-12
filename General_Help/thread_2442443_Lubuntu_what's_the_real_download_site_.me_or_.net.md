---
title: "Lubuntu: what's the real download site? .me or .net?"
date: 2020-05-03
forum: General Help
---

### Post by GhX6GZMB on 2020-05-03
There are two main Lubuntu sites that offer .ISO downloads: lubuntu.me and lubuntu.net.

So which is the correct one?
Until now, I've used lubuntu.me and am entertaining doubts. The .ISO files from there exhibit strange behaviour.

Can someone bring light into this, please.

Thank You.

---

### Post by howefield on 2020-05-03
lubuntu.me is the correct one to use.

---

### Post by jeremy31 on 2020-05-03
lubuntu.me is the official site according to [https://wiki.ubuntu.com/Lubuntu#Official_links](https://wiki.ubuntu.com/Lubuntu#Official_links)

---

### Post by CelticWarrior on 2020-05-03
You can check for yourself which one is official at [https://ubuntu.com/#download](https://ubuntu.com/#download) (spoiler alert: it's the .me)

> The .ISO files from there exhibit strange behaviour.
Please elaborate about the "strange behavior".

---

### Post by GhX6GZMB on 2020-05-03
> **CelticWarrior said:**
> 

Please elaborate about the "strange behavior".

I'm bit afraid to, because I've had a thread blocked on this subject due to repetitiveness.

The strange behaviour relates to fonts, this thread is one: [https://ubuntuforums.org/showthread.php?t=2442361](https://ubuntuforums.org/showthread.php?t=2442361)

I went a step further and booted from a (lubuntu.me) live DVD and opened LibreOffice Writer. Only Asian fonts, sigh.
So the problem is in the .ISO image, not my installation. For my live boot: language=default (English), keyboard=default (USA).

The Moderator suggested that I contact the "Lubuntu Team". I'm not quite sure how to, but have posted this issue on [https://discourse.lubuntu.me](https://discourse.lubuntu.me)
I've no idea whether this is the right approach.

---

### Post by CelticWarrior on 2020-05-03
> **ml9104 said:**
> I'm bit afraid to, because I've had a thread blocked on this subject due to repetitiveness.

The strange behaviour relates to fonts, this thread is one: [https://ubuntuforums.org/showthread.php?t=2442361](https://ubuntuforums.org/showthread.php?t=2442361)

I went a step further and booted from a (lubuntu.me) live DVD and opened LibreOffice Writer. Only Asian fonts, sigh.
So the problem is in the .ISO image, not my installation. For my live boot: language=default (English), keyboard=default (USA).

The Moderator suggested that I contact the "Lubuntu Team". I'm not quite sure how to, but have posted this issue on [https://discourse.lubuntu.me](https://discourse.lubuntu.me)
I've no idea whether this is the right approach.

Oh, if it's about that again, please don't.

---

### Post by GhX6GZMB on 2020-05-03
Like I said, I was hesitant about this. I really don't want to be a bore.

Still, is discourse.lubuntu.me the right way or how?

---

### Post by CelticWarrior on 2020-05-03
Yes, discourse.lubuntu.me seems to be the right place to air your grievances about Lubuntu having support for alphabets other than Latin (actually Etruscan/Roman) right from the start.

---

### Post by GhX6GZMB on 2020-05-03
@CelticWarrior:
Thank You. Your sarcasm and condescension has been noted.
That a Lubuntu installation has irrelevant fonts, but _no useful fonts_, is apparently normal to you.
I'll take care of my "grievances" myself, don't worry.
Consumer feedback to improve a product is seemingly also unwanted.

Cheers.

---

### Post by CelticWarrior on 2020-05-03
I don't have it currently installed but I recently tried it both in a live session and also as a trial/experiment in a very old laptop.
Everything in the desktop environment was in Latin alphabet, yours isn't? That means it comes with Latin fonts apt for said alphabet. Does it come with fonts for other alphabets as well? Probably, didn't check, but I assume it has and that's great. You can uninstall anything you don't need and install as many other fonts you want so I don't see a problem in including fonts for alphabets other than Latin. 

Now, "sarcasm and condescension"? Well, sarcasm perhaps - sometimes sarcasm is preferable to a direct confrontation of values that have no place in a modern society - but condescension?  I think you don't know the meaning of that word...

And "consumer feedback" Stephan Molineux style is surely unwanted.

---

### Post by GhX6GZMB on 2020-05-03
@CelticWarrior, I appreciate you coming  back with an open mind.
I'll repeat my problem: Lubuntu installs a lot of interesting fonts, but no relevant fonts. I have nothing against Tamil, but it's not useful to me. Here's my font listing after the latest reinstall:

```
macro@macro-pc:/usr/share/fonts$ cd truetype
macro@macro-pc:/usr/share/fonts/truetype$ ls -la
total 204
drwxr-xr-x 50 root root 4096 Okt 17  2019 .
drwxr-xr-x  8 root root 4096 Okt 17  2019 ..
drwxr-xr-x  2 root root 4096 Okt 17  2019 abyssinica
drwxr-xr-x  2 root root 4096 Okt 17  2019 ancient-scripts
drwxr-xr-x  2 root root 4096 Okt 17  2019 dejavu
drwxr-xr-x  2 root root 4096 Okt 17  2019 droid
drwxr-xr-x  2 root root 4096 Okt 17  2019 fonts-beng-extra
drwxr-xr-x  2 root root 4096 Okt 17  2019 fonts-deva-extra
drwxr-xr-x  2 root root 4096 Okt 17  2019 fonts-gujr-extra
drwxr-xr-x  2 root root 4096 Okt 17  2019 fonts-guru-extra
drwxr-xr-x  2 root root 4096 Okt 17  2019 fonts-kalapi
drwxr-xr-x  2 root root 4096 Okt 17  2019 fonts-orya-extra
drwxr-xr-x  2 root root 4096 Okt 17  2019 fonts-telu-extra
drwxr-xr-x  2 root root 4096 Okt 17  2019 fonts-yrsa-rasa
drwxr-xr-x  2 root root 4096 Okt 17  2019 freefont
drwxr-xr-x  2 root root 4096 Okt 17  2019 Gargi
drwxr-xr-x  2 root root 4096 Okt 17  2019 Gubbi
drwxr-xr-x  2 root root 4096 Okt 17  2019 hack
drwxr-xr-x  2 root root 4096 Okt 17  2019 kacst
drwxr-xr-x  2 root root 4096 Okt 17  2019 kacst-one
drwxr-xr-x  2 root root 4096 Okt 17  2019 lao
drwxr-xr-x  2 root root 4096 Okt 17  2019 liberation
drwxr-xr-x  2 root root 4096 Okt 17  2019 liberation2
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-assamese
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-bengali
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-devanagari
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-gujarati
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-kannada
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-malayalam
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-oriya
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-punjabi
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-tamil
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-tamil-classical
drwxr-xr-x  2 root root 4096 Okt 17  2019 lohit-telugu
drwxr-xr-x  2 root root 4096 Okt 17  2019 malayalam
drwxr-xr-x  2 root root 4096 Okt 17  2019 Nakula
drwxr-xr-x  2 root root 4096 Okt 17  2019 Navilu
drwxr-xr-x  2 root root 4096 Okt 17  2019 noto
drwxr-xr-x  2 root root 4096 Okt 17  2019 openoffice
drwxr-xr-x  2 root root 4096 Okt 17  2019 padauk
drwxr-xr-x  2 root root 4096 Okt 17  2019 pagul
drwxr-xr-x  2 root root 4096 Okt 17  2019 Sahadeva
drwxr-xr-x  2 root root 4096 Okt 17  2019 samyak
drwxr-xr-x  2 root root 4096 Okt 17  2019 samyak-fonts
drwxr-xr-x  2 root root 4096 Okt 17  2019 Sarai
drwxr-xr-x  2 root root 4096 Okt 17  2019 sinhala
drwxr-xr-x  2 root root 4096 Okt 17  2019 tibetan-machine
drwxr-xr-x  2 root root 4096 Okt 17  2019 tlwg
drwxr-xr-x  2 root root 4096 Okt 17  2019 ttf-khmeros-core
drwxr-xr-x  2 root root 4096 Okt 17  2019 ubuntu

```

The only Latin fonts are liberation and ubuntu, and those are what I see when using Lubuntu. Should I post a picture of the LibreOffice "Fonts" menu?

I've now been ridiculed by a couple of moderators (and you) on this issue, but it's no fun.

Concerning the Stephan whatever guy (never heard of him):
I've worked in sales and marketing all my life: when customers complain or have issues: it's a Good Thing (because they still believe in you and want you to solve the issue). If everything goes quiet, your business is down the drain.

---

### Post by QIII on 2020-05-03
And again, a duplicate.

Closed.

---

