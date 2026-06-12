---
title: "compiz acting strange"
date: 2008-04-27
forum: General Help
---

### Post by patmalcolm91 on 2008-04-27
i've been running hardy for a while now, and it's been running fairly stable (especially the last two weeks of development). i am constantly tweaking and changing my system, adding compiz plugins, etc.

After the upgrade on the 23rd, I restarted my computer, and when i logged into my name, i got crazy fragments in compiz(, and even metacity was affected). (see attachments for screenshots). The other user on this computer has not seen any of these side effects.

So I decided to reinstall all the compiz-based packages. This fixed the fragments, but now the animation plugin is broken. in ccsm, it says its enabled, but no animations actually happen on open/close/focus/minimize/etc.

Thanks for any help in advance. So far though, otherwise, hardy is awesome!:)

---

### Post by Zorael on 2008-04-27
There is the possibility of there still being remnants left from your old Compiz versions, messing things up. Did you use the **completely remove** option in Synaptic when uninstalling it? (equavilent to 'aptitude purge' and 'apt-get autoremove --purge')

Once uninstalled, if you want to be extra super sure, you could search your root partition for anything matching compiz and removing them manually.
```
$ sudo updatedb
$ locate compiz
```


That screenie looks like your videocard has a busted memory and is dying, though. :> Hopefully it's just something software-based.

---

### Post by patmalcolm91 on 2008-04-27
no, i didn't purge compiz, just reinstalled it. I'll go back and try again completely purging all the packages and reinstalling.
The laptop i'm on is almost 4 years old, so it might be the memory:( i hope not though. thanks.

---

### Post by patmalcolm91 on 2008-04-27
thanks, that seemed to work.

---

