---
title: "xine still slow despite DMA &amp; /etc/modules update"
date: 2005-07-08
forum: General Help
---

### Post by leperisland on 2005-07-08
Hello everyone - I am *very* new to Ubuntu and indeed Linux itself - please be gentle.

I have an AMD system, i run Ubuntu off a partion off my SATA drive. I have 2 DVD drives & 1gb of memory. I have  rage 128 graphics card & sound is provided by my onboard nVida card (although it's very muddy - any suggestions there?)

I am trying to watch DVDs in xine. Initially the playback was awful but after extensively going through forums I have managed to improve playback but it's still pretty out of sync.

Things I have done:

* Set DMA on my CD drive but not on my hard drive as it is SATA

* update /etc/modules so it reads:
amd74xx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod


Um that's about it really - please help i feel like I have tried everything!

Caroline

---

