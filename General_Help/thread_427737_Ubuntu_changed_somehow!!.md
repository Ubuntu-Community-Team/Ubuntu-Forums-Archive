---
title: "Ubuntu changed somehow!!"
date: 2007-04-29
forum: General Help
---

### Post by darmakwolf on 2007-04-29
I'm not completely new to the Ubuntu world, but all of a sudden my splash logo became Edubuntu and i'm using Ubuntu Fiesty! I rather liked the Ubuntu logo...

It was fine before. I didn't even do an update - it just changed on me. Is there either:
A: A program that lets me install *custom* logos
or B: A way to switch back to the original?

Any help much appreciated - thank you!!

---

### Post by floke on 2007-04-29
Delete the edbuntu artwork packages in synaptic.
That should zap it.

---

### Post by strabes on 2007-04-29
[http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/](http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/)

You can also just do this: ```
sudo aptitude remove edubuntu-artwork-usplash
```

---

### Post by Xappe on 2007-04-29
```

$ sudo update-alternatives --config usplash-artwork.so

```

choose the ubuntu usplash and then:

```

$ sudo dpkg-reconfigure linux-image-`uname -r`

```

---

### Post by darmakwolf on 2007-04-30
~ Thanks! ~

---

