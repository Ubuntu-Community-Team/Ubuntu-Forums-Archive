---
title: "GDM Resolution"
date: 2005-10-27
forum: General Help
---

### Post by Antioch on 2005-10-27
When I start up linux and am see the GDM login screen the resolution is lower than Id like, probablt 1240x... but I would like it to be 1600x1200. My xorg.xonf has only 1600x1200 listed as a possible resolution but I GDM still stays the same.

What should I do?

Ive attached my xorg.conf so you can take a look if you need to.

Thanks!

---

### Post by mykey on 2005-10-27
the modes in your xorg.conf are all comented and the only one that is working is incomplete - I just attach the corected version and you can check what was wrong

---

### Post by Antioch on 2005-10-27
Sorry, I was the one who commented the modes and made the last one incomplete in the hopes that it would only see 1600x1200 and use that - but it didnt work. But atleast GDM is running at 1600x1200, but there is still a problem.

Is there a way to change the frequency of the resoution at which GDM runs? I believe its trying to run at 75Hz, which shifts the screen to the right as well as makes things look fuzzy - but it needs to run at 60Hz. Is there a line I can put in the xorg.conf?

"VertRefresh     60" doesnt work. xorg complains its invalid and wont start unless I remove it.

---

### Post by Antioch on 2005-10-27
I solved my problem. I put VertRefresh and HorizSync in the wrong section of the xorg.conf. Now things work beautifully.

Thanks for all the help!:D

---

