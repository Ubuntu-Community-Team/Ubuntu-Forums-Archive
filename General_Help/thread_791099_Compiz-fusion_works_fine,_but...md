---
title: "Compiz-fusion works fine, but.."
date: 2008-05-11
forum: General Help
---

### Post by miickEe on 2008-05-11
I recently reinstalled ubuntu because some programs I installed under wine became unstable.

Anyways, before the reinstallation I had all my desktop effects working flawlessly.

Just to clarify, my specs are:
AMD 64 Althon 3200+
Asus K8V Deluxe MB
Nvidia Geforce FX 5200 GFX

And now after the reinstallation of ubuntu and subsequent software to enable the previous desktop effects, it runs like a dog. Like, literally. System Monitor tells me it's running more than 50% of the resources, which is insane. It wasn't doing this before so I don't know why it's doing it now.

Any help, suggestions, solutions?

---

### Post by russo.mic on 2008-05-12
seems to me that reinstalling ubuntu because wine was being unstable is a bit like buying a new car because you've got a flat..but that's just my opinion.  

Anyway, Do you have XGL running on top of the new ATI driver with direct rendering on?  that could easily cause that.  if your using the new atidriver, make sure that the xserver-xgl package is NOT installed.

Russo

---

### Post by miickEe on 2008-05-12
Thanks for the reply mate.

I don't know if I do, so how would I check? And if that is not the case, then what would it be? How would I go from there?

---

### Post by miickEe on 2008-05-12
Okay, I put in this command:
glxinfo | grep direct
And my response was : "Direct Rendering: Yes"

I also put this one in : glxinfo | grep version
And the response was: "OpenGL version string: 2.1.2 NVIDIA 169.12"

---

### Post by Ocxic on 2008-05-13
try running wine with a virtual desktop

---

### Post by miickEe on 2008-05-13
Not much help.

---

