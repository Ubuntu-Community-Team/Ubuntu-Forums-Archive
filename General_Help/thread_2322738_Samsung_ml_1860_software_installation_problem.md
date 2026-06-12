---
title: "Samsung ml 1860 software installation problem"
date: 2016-04-30
forum: General Help
---

### Post by george11 on 2016-04-30
Often a problem with this printer, but absolutely no joy installing in 15.10 mate.  Please help.  I'm a novice so detailed instruction help.  Thank you.

---

### Post by $yl9pAR%t on 2016-04-30
1. Download Print Driver from Samsung website ([www.samsung.com](www.samsung.com)).
2. Go to Download directory, right click on downloaded file and choose "Extract here".
3. Now you should have new directory, probably named "uld".
4. Right click this "uld" directory and choose "Open in Terminal"
5. Run this command:

```
sudo sh install-printer.sh
```

6. You will have to accept EULA and answer a few questions.
7. After installation completed you can switch on your printer.
8. If after a few seconds your OS will not find and install your printer automatically, go to Printers application and do it manually.

---

### Post by kurt18947 on 2016-04-30
I have a Samsung B & W multifunction so this thread tweaked my interest. I went to Samsung's linux download site and looked at drivers by model. I think there's one unified laser driver for many Samsung printers. 

[http://www.samsung.com/us/support/downloads#Printers](http://www.samsung.com/us/support/downloads#Printers)

I see listed models ML-1750 and ML-1865, no ML-1860 in monochrome laser printers. Perhaps that model is sold in Europe or Asia? I'd probably go with ML-1865.

---

### Post by $yl9pAR%t on 2016-04-30
> **kurt18947 said:**
> 
I see listed models ML-1750 and ML-1865, no ML-1860 in monochrome laser printers. Perhaps that model is sold in Europe or Asia? I'd probably go with ML-1865.

Yes, ML-1860 is sold (or rather was) in Europe and driver for it is available on Samsung website. From my localization (Europe) the driver for exactly ML-1860 is listed. This printer works faultlessly on Ubuntu 14.04 and Ubuntu 16.04, I have no idea about 15.10.

---

