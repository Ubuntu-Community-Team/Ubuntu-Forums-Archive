---
title: "Graphical Errors in 12.10 [Fresh Install]"
date: 2012-11-13
forum: General Help
---

### Post by Verathis on 2012-11-13
I'm getting some odd graphical errors in 12.10. I wasn't able to capture a screenshot of the issue as it seems to fix itself when I try to take one, so I had to take a picture with my phone.

[http://i.imgur.com/6Nycs.jpg](http://i.imgur.com/6Nycs.jpg)

The issues are fairly obvious upon seeing the picture. The icons at the top are rather messed up, as is some of the text. This was happening during the install process as well.

My video card is an nVidia GeForce GTX 460M. I'm using the Nouveau drivers.


Edit: This happens in more than the Software Center. It was also happening in the address bar in Chrome, as well as other random spots.

---

### Post by 1204 on 2012-11-14
Have you tried official drivers? [http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by philinux on 2012-11-14
> **Verathis said:**
> I'm getting some odd graphical errors in 12.10. I wasn't able to capture a screenshot of the issue as it seems to fix itself when I try to take one, so I had to take a picture with my phone.

[http://i.imgur.com/6Nycs.jpg](http://i.imgur.com/6Nycs.jpg)

The issues are fairly obvious upon seeing the picture. The icons at the top are rather messed up, as is some of the text. This was happening during the install process as well.

My video card is an nVidia GeForce GTX 460M. I'm using the Nouveau drivers.


Edit: This happens in more than the Software Center. It was also happening in the address bar in Chrome, as well as other random spots.

Try installing nvidia-current. Search sources in Dash and open software sources. End tab is additional drivers. Choose nvidia current. That will install the proprietary driver.

---

### Post by Verathis on 2012-11-14
I did try the nvidia-current drivers last night and they didn't seem to solve the issue. However, it seems to have fixed it today. Perhaps I derped out last night and was trying one of the experimental drivers instead of current. Who knows?

Oh well, thanks for the assistance!

---

