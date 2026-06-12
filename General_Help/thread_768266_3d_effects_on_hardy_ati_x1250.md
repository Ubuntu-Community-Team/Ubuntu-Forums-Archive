---
title: "3d effects on hardy ati x1250"
date: 2008-04-26
forum: General Help
---

### Post by soumen08 on 2008-04-26
Hi,
I have just installed hardy heron on my hp6515b laptop and 3d effects are not working. On the beta 3 release, which i had installed too, i just had to click Extra on the Appearance>Effects whereupon it downloaded a package called xorg-driver-fglrx and installed it and i had 3d effects running. By the way i have noticed that the advanced desktop effects settings arent there in the appearence menu as they used to be in the beta. do i have to install compiz before it will work? since they had fixed it in the beta, i had expected it to be running on the stable release. Can someone help?
Thanks,
Soumen

---

### Post by Zorael on 2008-04-26
Compiz nowadays reject laptops with ati cards, so you'll likely need to force it to start. Anyway, to make sure, could you post the terminal output of the following command?
```
$ compiz --replace &
```

---

### Post by soumen08 on 2008-04-27
well it isn't required anymore. I noticed that the restricted driver for fglrx wasn't loaded and thus it couldn't do it after i enabled the driver the thing works just fine.

I had tried compiz replace but the thing defaulted to metacity repeatedly.
Thanks.

---

