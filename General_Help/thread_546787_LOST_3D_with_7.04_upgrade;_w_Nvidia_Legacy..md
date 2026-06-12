---
title: "LOST 3D with 7.04 upgrade; w/ Nvidia Legacy."
date: 2007-09-09
forum: General Help
---

### Post by Neobuntu on 2007-09-09
Not dist-upgrade (or managed), but a regular upgrade. I'm getting that glx isn't working. I reinstalled two different kernel images (with restricted drivers; legacy Nvidia) and nothing works accelerated. The legacy card I have is a Geforce2.

I saw Nvidia leagcy update come through and bam! All 3D is up in flames(actually no flames). It's concerning that so many apps do not work now.

---

### Post by Neobuntu on 2007-09-09
Is this a system-wide issue?

---

### Post by Neobuntu on 2007-09-10
Everybody else has direct 3D graphics that has an legacy Nvidia card?

---

### Post by Neobuntu on 2007-09-12
OK I fixed it (anyway).

I noted a "restricted-manager" or something like that and it did not run. I reinstalled it and it then ran. 

I unchecked my enabled (but not working) Nvidia 3D.

Then I checked enable. It loaded all manner of "stuff" and I was concerned that it didn't do the legacy card, but it worked. The refresh rate is reading a bit off and I don't know what's up with that, but I do have it working; overall.  2.6.20-16-generic #2 SMP

Do I get extra credit for answering my own posts? (:

---

