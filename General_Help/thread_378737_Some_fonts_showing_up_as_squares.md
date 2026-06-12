---
title: "Some fonts showing up as squares?"
date: 2007-03-07
forum: General Help
---

### Post by Eupham on 2007-03-07
I was trying to install kiba dock and did something stupid.  To make things short, I followed a guid that said to run

```
sudo aptitude install cvs automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev checkinstall libglade2-dev libxcomposite-dev libtool 
```

Before I could stop it I saw many things being removed.  Now I've gotten most things back to normal but some text shows up as squares.  If i see this I assume it is just some missing fonts. 
[B]
I was wondering if it is possible to reinstall the normal ubuntu/kubuntu fonts through apt-get or something?  Please help.[/B]

---

### Post by fragos on 2007-03-07
Run Synaptic and search for "ttf-".  You can choose from these but you don't need them all.  Some I would use are ttf-dejavu, ttf-bitstream-ver and ttf-freefont.

---

