---
title: "Need help using unshield...pwetty pwease :)"
date: 2007-04-13
forum: General Help
---

### Post by giambrone on 2007-04-13
Okay, so I'm trying to extract the file "data1.cab" so that I can use drivers from it to get ndiswrapper going with my wireless card. I've tried using cabextract - it worked on the ".exe" but I'm gathering this .cab is done in InstallShield. On installing unshield I discovered what a n00b I am - and i'm stumped at how to use it...

Any help much appreciated :)

Thanks,
Matt:KS

---

### Post by jputman01 on 2007-04-13
it doesnt work if you 'cd' to the directory of the .cab file and run
```
sudo unshield name-of-file.cab
```

---

### Post by giambrone on 2007-04-13
So I see!!
How *do* I do it then??

Matt:KS

---

### Post by giambrone on 2007-04-13
Okay... So far I worked out unshield x (and drag the file into terminal) - it came up with the error > matt@matt-desktop:~$ sudo unshield x '/home/matt/Desktop/data1.cab' 
Failed to open /home/matt/Desktop/data1.cab as an InstallShield Cabinet File


...What do I do now?????
EEP.

Matt:KS

---

### Post by giambrone on 2007-04-13
Okay... Happy now - Problem solved - I hadn't tried data1.hdr, but when I did it worked...
Thanks anyway ;D

Matt:KS

---

