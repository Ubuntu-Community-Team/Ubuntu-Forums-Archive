---
title: "[SOLVED] Problem getting my nvidia driver working."
date: 2008-05-19
forum: General Help
---

### Post by S3loth on 2008-05-19
I have a NVIDIA GeForce 6150 LE. Ever since updating to 8.04 compiz or anything fancy doesn't work. I looked in the restricted drivers and it doesn't come up. How would I install it manually?

---

### Post by Zacariaz on 2008-05-19
I had similar problems, however I found that the driver was in fact installed, but not activated as it was a restricted driver.
Is this is the case for you also all you have to do is open "System-> Hardware Drivers" from your applications menu, check the enable box and press apply or something similar.

---

### Post by mmb1 on 2008-05-19
If using the restricted drivers manager doesn't work, try using a driver management and installation program called "envy", it should be available through synaptic.

---

### Post by Victormd on 2008-05-19
use Envy-NG and that should do the trick...

---

### Post by Lukky on 2008-05-19
If you Look on the NVIDIA page there should be a Linux driver there for it. Just follow the install steps or post back when you have problems.

Thanks Dustin

---

### Post by S3loth on 2008-05-20
When I try to install the nVidia drivers it tells me to exit X-server. I read that to do this you push Ctrl+Alt+F1, however when I do this it takes me to a blank screen with only a "_" flashing in the top left, and freezes like that. Any other way to shut down X-server?

---

### Post by S3loth on 2008-05-20
Bump

---

### Post by bzoomer16 on 2008-05-20
> **mmb1 said:**
> If using the restricted drivers manager doesn't work, try using a driver management and installation program called "envy", it should be available through synaptic.

I totally agree. Envy is amazing for people having trouble with graphics cards. I actually killed mine so bad that I couldn't get the X Server to work and so I resorted to using the text-based option for Envy...it's really quite versatile in terms of compatibility and so forth. :)

---

### Post by S3loth on 2008-05-20
Alright, trying Envy now. When I try to install with envy it gives me this error:

There was an error in the installation process. You can see the log file /var/log/envy-installer.log

Then when I go to termanal and type gedit /var/log/envy-installer.log I get this:

python pulse.py nvidia 
root@revolution:/usr/share/envy# python pulse.py nvidia
ENVY ERROR: Your Operative System does not seem to be supported by Envy

Any ideas? :(

---

### Post by rocknrolf77 on 2008-05-20
Did you install envy-ng. The regular envy is the legacy version and will not work in 8.04.

---

