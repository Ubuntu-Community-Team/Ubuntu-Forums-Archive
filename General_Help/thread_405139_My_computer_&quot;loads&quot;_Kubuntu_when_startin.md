---
title: "My computer &quot;loads&quot; Kubuntu when starting! (I use Ubuntu)"
date: 2007-04-09
forum: General Help
---

### Post by Fireblend on 2007-04-09
I downloaded kubuntu-desktop with aptitude yesterday to try it out. After a few mins of playing around I decided I could put those 160 MBs to better use and decided to remove. Again with Aptitude, I removed desktop-kubuntu and I had no problems until now that I restarted my computer and the loading screen says it's Kubuntu >_>
Any way to revert it to the regular Ubuntu screen?

Thanks in advance!

---

### Post by solar george on 2007-04-09
Try this,

```
sudo apt-get remove kubuntu-artwork-usplash
sudo apt-get install usplash-theme-ubuntu

```

---

### Post by Fireblend on 2007-04-09
Nope, not working. Kubuntu-artwork-usplash wasn't installed and Usplash-theme-ubuntu was already there >_>

---

### Post by strabes on 2007-04-09
You just somehow installed the kde usplash image. Just run this command and select the ubuntu one. ```
sudo update-alternatives --config usplash-artwork.so && sudo dpkg-reconfigure linux-image-`uname -r`
```

When you restart it should be fixed. If it isn't, just do this: ```
sudo rm /usr/lib/usplash/usplash-theme-kubuntu.so && sudo dpkg-reconfigure linux-image-`uname -r`
```

That will delete the kubuntu one from your system.

---

### Post by Fireblend on 2007-04-09
> **strabes said:**
> You just somehow installed the kde usplash image. Just run this command and select the ubuntu one. ```
sudo update-alternatives --config usplash-artwork.so && sudo dpkg-reconfigure linux-image-`uname -r`
```

When you restart it should be fixed. If it isn't, just do this: ```
sudo rm /usr/lib/usplash/usplash-theme-kubuntu.so && sudo dpkg-reconfigure linux-image-`uname -r`
```

That will delete the kubuntu one from your system.

Ah, that worked! Thanks a lot :D
And that's an awesome Muse avatar :p

---

