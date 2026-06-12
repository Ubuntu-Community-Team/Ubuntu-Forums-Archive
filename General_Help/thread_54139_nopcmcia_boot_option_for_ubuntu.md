---
title: "nopcmcia boot option for ubuntu?"
date: 2005-08-03
forum: General Help
---

### Post by notebooktessler on 2005-08-03
Hi, 

I'm trying to boot my notebook from the live cd but there is a problem
with the pcmcia detection - the computer freezes when loading "PC card
services". 

In Knoppix, I simply boot with the "nopcmcia" option, but Ubuntu does
not seem to recognize this option, neither "pcmcia=off". Is there a
simple way to prevent Ubuntu from loading pcmcia? 
The expert mode seems too timeconsuming and complicated for me... I want an
automatic boot without pcmcia! 

Thanks for any suggestions,
Ludwig

---

### Post by hypnos on 2005-08-05
Try:

live hw-detect/start_pcmcia=false

It will not search PCMCIA card.

---

### Post by notebooktessler on 2005-08-05
Hey thanks, that's what I was looking for! 

Unfortunately Ubuntu now freezes as soon as X is started... I'm not sure whether I should risk an installation. 

(Interestingly, I also tried Kubuntu but the nopcmcia option doesn't prevent it from starting pcmcia at all.) 

Thanks anyway, 
ludwig

---

### Post by helsby on 2005-08-06
mine doesnt freeze but does eventually go to a black screen, beeps and 3 minutes later switches itself off.
I'm using a toshiba 2065cds screen

---

