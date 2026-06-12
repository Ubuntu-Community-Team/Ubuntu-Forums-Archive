---
title: "Usplash theme unchanged after upgrade to Edgy"
date: 2006-10-31
forum: General Help
---

### Post by timothyM on 2006-10-31
Hello,

I had been running the beta release of Edgy on my computer, which I installed when it was still using the placeholder theme for usplash - the one with the brown background at 640x480.

I have apt-get dist-upgrade to the full version of Edgy, but I still have this usplash theme on boot. When I shutdown I get the new style one, however.

I have tried dpkg-reconfigure on usplash and reinstalling the ubuntu theme for it, but I still get the old boot theme.

If anyone can tell me how to switch to the new theme, I'd be very greatful, (the old one is a bit of an eyesore in the morning).

Thanks.

---

### Post by louis_nichols on 2006-10-31
I would just reinstall the usplash-ubuntu theme from synaptic.

I ran through similar problems, updating from dapper to breezy.

---

### Post by timothyM on 2006-10-31
I'd tried reinstalling the theme, but that had failed to change anything. Turns out for the theme to have effect you have to:

```
sudo update-alternatives --set usplash-artwork.so /usr/lib/usplash/usplash-theme-ubuntu.so
```

then

```

sudo dpkg-reconfigure linux-image-`uname -r`

```

Then it's magically changed upon boot :)

---

