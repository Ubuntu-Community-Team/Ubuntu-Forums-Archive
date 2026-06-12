---
title: "(Oh) Brother MFC Printing Issue"
date: 2008-01-23
forum: General Help
---

### Post by Ian505 on 2008-01-23
I have a problem with my MFC-5460CN printer from Brother. I installed Brother's Drivers and I can print and everything... the only problem is printing is SOO SLOW! About 3x slower than if I print it from windows. It seems like the printer only gets small chunks of data, prints it, and then tells Ubuntu (7.10) that it's done and CUPS sends the next packet. But that pause doesn't happen when I print from Windows! Is there a setting I can tweak to tell CUPS that the memory in this machine is much larger than the packets it's sending? Or is it something else? I am new at this, so please be patient with me. 

Thanks,
Ian

---

### Post by Shazaam on 2008-01-23
Type this into a browser and you can manage your printer (might want to bookmark it too)...

[http://127.0.0.1:631/](http://127.0.0.1:631/)

This will get you to the local cups admin page. Check your settings from there.

---

### Post by Ian505 on 2008-01-23
It only gets me the settings that I can adjust in the System->Administration->Printing menu, and none of those can fix this problem. (It's all alignment and color/photo settings- and the different settings don't affect printing speed, I've tried.)

Any other suggestions?
-Ian

BTW- Thanks for the CUPS address.

---

