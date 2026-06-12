---
title: "[SOLVED] burn a bootable cd, how?"
date: 2007-07-02
forum: General Help
---

### Post by T0MA on 2007-07-02
Hey everyone, 
I've just tried to burn a bootable cd of feisty to install it on another computer with GNOME Baker, but the cd wasnt bootable... any idea how can I burn a bootable cd? I found no such option in gnome baker.

thx!

---

### Post by Junx on 2007-07-02
Well, if nobody can figure this out, I recommend just getting K3b.  Sure, it's a KDE program (and I'm a KDE user ;p), but it is superb and most certainly supports making bootable CDs.

If you're burning an ISO image, I would have assumed that Gnome Baker makes it bootable by default considering the image itself specifies that I believe.

---

### Post by khedron on 2007-07-02
I use Kubuntu, so the program I'd use is called K3b. This definitely can burn bootable images. Install it with this command:
```
sudo aptitude install k3b
```or use synaptic to install it.

Then open it and select Tools>Burn CD Image...
Select the image file and make sure you are burning to the right CD drive. Then press start. The burning should take about 30 minutes, depending on how fast your drive is.

If this doesn't work, write here again and we'll try and sort something out.

(Were you burning the image as a file or an image? Burning it as a file stops it from being bootable. This is the usual reason burning boot CDs doesn't work for people.)

EDIT: Junx, you beat me to it. Well, my post has instructions, so :p

---

### Post by T0MA on 2007-07-02
i mounted the iso file and then just copy-pasted everything from the mounted dir to the cd... guess ill try k3b, thx folks

---

### Post by franck3d on 2007-07-02
if you right click on your .iso you should be given the option to burn to disc.
not at my ubunutu box right now but i think this is how it works for me.

---

### Post by louieb on 2007-07-02
> **franck3d said:**
> if you right click on your .iso you should be given the option to burn to disc.
not at my ubunutu box right now but i think this is how it works for me.
Dittos:  in Gnome (Nautilus) its that easy.

---

