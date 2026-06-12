---
title: "Shutter (screenshot app) extremely slow."
date: 2014-08-30
forum: General Help
---

### Post by 2CV67 on 2014-08-30
I have used Shutter for years on my old 32-bit PC & like it a lot.
It was still working OK in 14.04 Xfce when that PC was retired last week.

But on installing Shutter in my new 64-bit PC with Ubuntu 14.04.1 Unity, it has a big problem - several operations take up to 45 seconds!

Most obviously, when you click on "Selection", then it takes 45 seconds before the screen with selection cross appears.
Then, after taking the screenshot, it often takes 7 seconds before the result appears.

Clicking on the option "Window" results in an immediate screenshot (I think), but the results take 15-30 seconds to appear.

Using the option "Desktop" similarly produces instant reaction, but the results take around 50 seconds to appear.

On this same PC I have a small partition with another Unity 14.04.1 in standard condition, so I just installed Shutter there to check.
I found almost identical results.

All suggestions welcome!

---

### Post by ibjsb4 on 2014-08-30
Have you searched for an alternative video driver?

Also for testing purposes you could install the 'flashback desktop'.
```
sudo apt-get install gnome-panel
```

---

### Post by 2CV67 on 2014-08-31
I tried installing Xfce in my spare 14.04.1 partition, but the results were just the same.

Following your suggestion, I went to System Settings > Software & Updates > Additional Drivers:

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/2d172a24-f74b-4165-914a-4bf91a2e53cb_zps5a143b03.png[/IMG]

I seemed to be using the recommended driver, but opted for the first proprietary one in the list.

The results are completely satisfactory!
All responses are now immediate.

Thank you very much for that excellent advice!  :D

---

### Post by ibjsb4 on 2014-08-31
Now if we could just do something about that car :p

---

### Post by 2CV67 on 2014-08-31
...being extremely slow too, you mean?

That's all part of the charm. ;)

---

