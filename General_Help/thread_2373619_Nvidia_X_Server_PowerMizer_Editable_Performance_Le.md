---
title: "Nvidia X Server PowerMizer Editable Performance Levels"
date: 2017-10-07
forum: General Help
---

### Post by ubuntini2 on 2017-10-07
Using Coolbits to expose the editable performance levels in powermizer.

But how do I know what values to try?

Both for
1 Graphics Clock Offset

and

2 Memory Transfer rate Offset

---

### Post by efflandt on 2017-10-08
Experiment gradually, and run some intensive graphics benchmark like Unigine Heaven with extreme settings (which does a bit heavier test than Unigine Valley). When you enter numbers (which is offset, not total frequency) hit Enter for each change to take effect (you should see numbers change above).  If you start seeing artifacts (like zooming too much into a jpg file), back off. Some graphics cards like GTX 750 Ti or GTX 1050 Ti may be hardware regulated to a maximum number of watts to operate without auxiliary power, so for those you may start dropping occasional frames as you increase and they hit their power limit before actually seeing artifacts, and you want to back off to the point that you do not lose frames.

When I had an MSI Twin Frozr Gaming GTX 750 Ti OC that was factory overclocked, I could easily bump its GPU another 220-240 MHz, although, that only increased a few fps. Bumping memory speed did not seem to make much difference. I have not experimented much with my Asus Dual GTX 1060 OC because it works well as is (significantly faster than GTX 750 Ti). Its factory OC may be close to max, it holds that speed, but when I bumped its GPU 100 MHz it was faster initially, but decreased back down some as it heated up. I have not tried also bumping up fan speed (which would remain at a manual setting and not adjust automatically).

---

### Post by #&amp;thj^% on 2017-10-08
I use a value of "12" with my NVIDIA GF114 [GeForce GTX 560 Ti]
which gives me Fan Control && Clock Offset && Memory Transfer Rate Offset.

I would also warn of setting values to high, as some cards manufactured are not of the same quality seen by bigger names.


efflandt gives great advice on slowly changing these settings by hand. (Testing First)
Good Luck.

---

