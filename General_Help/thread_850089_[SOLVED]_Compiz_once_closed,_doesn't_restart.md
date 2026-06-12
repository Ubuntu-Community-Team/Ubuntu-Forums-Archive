---
title: "[SOLVED] Compiz once closed, doesn't restart"
date: 2008-07-05
forum: General Help
---

### Post by sayakb on 2008-07-05
Dealing with a 1 year old laptop (T5500, 1GB RAM, Intel GMA950/945GM Onboard, 320GB HDD) here.

If I switch to metacity, I cant switch back to compiz unless I restart X.

```
glade@Mean-Machine:~$ compiz --replace &
[2] 10547
glade@Mean-Machine:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

Once I restart X, it works normally again. I have tried Compiz fusion icon and Compiz-switch. Neither of them work for me.
Any ideas?

---

### Post by Tomatz on 2008-07-05
> **LinuxIsInnovation said:**
> Dealing with a 1 year old laptop (T5500, 1GB RAM, Intel GMA950/945GM Onboard, 320GB HDD) here.

If I switch to metacity, I cant switch back to compiz unless I restart X.

```
glade@Mean-Machine:~$ compiz --replace &
[2] 10547
glade@Mean-Machine:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

Once I restart X, it works normally again. I have tried Compiz fusion icon and Compiz-switch. Neither of them work for me.
Any ideas?


Shouldn't xgl be running with that gpu? Is it usually running when compiz is?

---

### Post by sayakb on 2008-07-05
The previous output was **after** I once fired metacity --replace.
Now this one I fired with compiz running already. I still have compiz after this, (since I have'nt switched to metacity yet, as mentioned above)
```
glade@Mean-Machine:~$ compiz --replace &
Checking for Xgl: [2] 29072
glade@Mean-Machine:~$ not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

[1]-  Done                    compiz --replace
glade@Mean-Machine:~$ 

```

---

### Post by Tomatz on 2008-07-05
I think you may have metacity's composite manager enabled. The compiz-check script i have attached should help you fix the issue. You must run it with metacity enabled. ;)

---

### Post by sayakb on 2008-07-05
Bravo!
The problem was simple enough! Metacity was running in background and compiz wasn't able to run with metacity running. I have to terminate metacity to start compiz (Which the --replace should do, but it isn't doing). So I simply do a **killall metacity** before firing compiz --replace again
Thanks for the script. Very useful script indeed!

---

### Post by Tomatz on 2008-07-05
> **LinuxIsInnovation said:**
> Bravo!
The problem was simple enough! Metacity was running in background and compiz wasn't able to run with metacity running. I have to terminate metacity to start compiz (Which the --replace should do, but it isn't doing). So I simply do a **killall metacity** before firing compiz --replace again
Thanks for the script. Very useful script indeed!

Cool ;)

Glad i could help.

---

### Post by ovidiub on 2008-08-12
Thanks for the script. Solved my problem too. Cheers

---

