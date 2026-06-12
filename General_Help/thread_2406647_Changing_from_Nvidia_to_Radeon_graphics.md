---
title: "Changing from Nvidia to Radeon graphics"
date: 2018-11-23
forum: General Help
---

### Post by Autodave on 2018-11-23
I was running an Nvidia GPU using the 390 driver from the repositories.  I removed that and installed a Radeon GPU which is giving me better performance.  I have not removed the Nvidia driver.  Do I need to?  How?

Do I need to install anything for the Radeon RX 460 card?  (It seems to be working great.)

---

### Post by Autodave on 2018-11-25
bump

---

### Post by Autodave on 2018-11-27
bump

---

### Post by wildmanne39 on 2018-11-27
*Thread moved to **General Help for a more appropriate fit**.*

---

### Post by mastablasta on 2018-11-28
if it works leave it. 

AMD: [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

you can purge the nvidia driver. but it depends on how you installed it.
nvidia:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

---

### Post by Autodave on 2018-11-28
if it works leave it.......

I almost did exactly that.  But, I am glad now that I didn't. Removed the Nvidia driver and installed the amdgpu-pro driver.  FANTASTIC difference.  Well worth the extra work even though I haven't played with command line installation of anything in the last 10 years! :-)

Thank you soooo much!

---

