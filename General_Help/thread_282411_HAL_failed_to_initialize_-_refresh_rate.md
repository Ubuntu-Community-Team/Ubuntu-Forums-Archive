---
title: "HAL failed to initialize - refresh rate"
date: 2006-10-22
forum: General Help
---

### Post by DE Retiree on 2006-10-22
Hi people, I'm a relative new linux and Ubuntu user. I posted this in the Edgy forum, but got no responses so I thought I'd try here.  

I am running Edgy on an old Gateway PII 400 with 384 megs memory and an STB128 4meg video card. I installed the Edgy daily build on October 13 and have installed the recommended updates several times since then - all the standard repositories are enabled except "source" and I installed Automatix2 to get Firestarter firewall a couple of days ago. 

This morning I installed the latest updates and after the suggested reboot, I got the title error message (Failed to initialize HAL). Now my monitor, a Gateway VX900, has only a 60hz refresh rate at 1024 x 768 vs the 85hz before the reboot. I searched for HAL topics but did not find anything that seemed applicable. Any suggestions?

.... DE Retiree

---

### Post by DE Retiree on 2006-10-22
"Sort of" solved my problem.  I reinstalled Dapper and refresh rate returned to 85HZ.  Someone in the Edgy crowd must have decided my old machine was not worth being able to run Edgy and changed a config file????  I looked in the xorg.conf file in Edgy and the latest updates showed my monitor as a generic with a max refresh rate of 60HZ.  No longer would identify my Gateway VX900 monitor like the previous releases of Edgy and Dapper did.

Oh well .......

---

