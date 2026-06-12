---
title: "Uninstall..."
date: 2015-01-04
forum: General Help
---

### Post by Furycd001 on 2015-01-04
HI Guys

Is it possible on ubuntu 14.10 to remove / uninstall all apps / unity lenses that come pre installed with ubuntu. If possible could someone please tell me how to do it. If it is not possible then could someone tell me how I can installed minimal unity from a minimal iso.


Many thanks...

---

### Post by cariboo on 2015-01-04
To uninstall packages, I'd suggest using synaptic package manager, as I find the Software Centre rather clunky.  Once you have synaptic installed, click the status button, then browse through install packages. You can also use the search function if you know the name of the packages you want to remove.

---

### Post by Furycd001 on 2015-01-04
Thank you for your reply. I usually just uninstall software centre and use synaptic because I find synaptic runs a lot better. Was really just asking in case there was a better option on the cards.

---

### Post by grahammechanical on 2015-01-04
I do not think that there is such a thing as a minimal Unity for Unity is part and parcel with the Ubuntu Desktop. So, we need to be aware that we do not remove the ubuntu desktop as that would break the OS. Unless we have previously installed an alternative as a back up.

If you search Synaptic Package Manager for "scope" you will find some of the scopes that are installed.

Regards.

---

### Post by ian-weisser on 2015-01-04
> **jonny6 said:**
> Is it possible on ubuntu 14.10 to remove / uninstall all apps / unity lenses that come pre installed with ubuntu.

It's possible to uninstall some, but not all.
Try removing the unity-webapps-*, unity-scope-*, and unity-lens-* packages.

READ CAREFULLY what will be removed when you do this. You may unintentionally remove all of Unity, breaking your GUI environment and limiting you to text console until you repair the damage.

> **jonny6 said:**
> how I can installed minimal unity from a minimal iso.

The 'unity' package is pretty close to what you seem to be looking for.
Of course, it may not fully functional without some of the "extra" stuff.

---

