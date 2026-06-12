---
title: "Installing Xubuntu Splash"
date: 2006-11-07
forum: General Help
---

### Post by Sethro on 2006-11-07
I liked to Xubuntu slash screen because of the blue colour and I opened up Terminal and did this:

sudo aptitude install xubuntu artwork (something )

and everything worked perfectly! Yay

When I shut down I got the pretty Xubuntu splash, but when I started my computer again the original ubuntu splash shows up

How can I fix it?

---

### Post by Ramses de Norre on 2006-11-07
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure usplash
```

---

### Post by autocrosser on 2006-11-07
Or look back thru the Edgy-development forum for Usplash-Switcher--there is some great artwork you can get too...

Switcher is "slated" for inclusion with Fawn!!!!

---

### Post by Sethro on 2006-11-07
> **Ramses de Norre said:**
> ```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure usplash
```

Yup thanks that did it, 

:)

---

