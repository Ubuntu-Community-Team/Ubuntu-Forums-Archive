---
title: "Cant update/add extentions/themes in Firefox"
date: 2005-09-02
forum: General Help
---

### Post by mark2 on 2005-09-02
If i use the "Get extentions/themes" thing in Firefox, it just sends me to the update page, and i downloaded the "latest" version, and it wouldnt install *grr* so i guess i'm stuck now? (newbe btw)

I really wanna download my fav firefox extention = Adblock

---

### Post by sethmahoney on 2005-09-02
This is a known issue with the Ubuntu version of Firefox.  There's a fix on mozilla's page, but it doesn't work for me.  My suggestion is to fire up Synaptic and see if you can find adblock in there (I was surprised to find StumbleUpon and a couple other moz extensions).

---

### Post by mark2 on 2005-09-02
[QUOTE=sethmahoney]This is a known issue with the Ubuntu version of Firefox.  There's a fix on mozilla's page, but it doesn't work for me.  My suggestion is to fire up Synaptic and see if you can find adblock in there (I was surprised to find StumbleUpon and a couple other moz extensions).[/QUOTE]

I got it to work now, hehe... about:config then...

general.useragent.vendorSub = 1.0.6

Also to be safe i changed general.useragent.vendorComment to 1.0.6

And it works sweetas for me now :)

Look, a newbe teaching :D

---

### Post by shakin on 2005-09-02
Using Firefox 1.0.6 from the backports repo should also work, plus you get the real 1.0.6 version.

---

### Post by Elrohir on 2005-09-03
**apt-get upgrade** made the trick some weeks ago... downloaded 1.0.6 and no problems since then...

what I'm wondering is that when 1.5 comes out, will it be uploaded to the backports or the other sources inmediately?? :?

---

