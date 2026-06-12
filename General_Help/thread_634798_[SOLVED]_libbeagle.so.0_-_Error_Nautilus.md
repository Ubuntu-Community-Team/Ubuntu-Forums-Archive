---
title: "[SOLVED] libbeagle.so.0 - Error Nautilus"
date: 2007-12-08
forum: General Help
---

### Post by pcolamar on 2007-12-08
Nautilus is not working any longer.
I got the following msg when run from a terminal:

**nautilus: error while loading shared libraries: libbeagle.so.0: cannot open shared object file: No such file or directory**


I tried to reinstall the libbeagle.so.0 but nothing changes and I actually do not find the libbeagle.so.0 where it is supposed to be (/usr/lib/libbeagle.so.0).
Strange enough, Synaptic says that it is not Authenticated when I reinstalled it.

Any help ?

Thanks

Palmer

---

### Post by pcolamar on 2007-12-08
Ok, I found the problem.

For whatever reason the source repository Synapsys was using was

[http://ppa.launchpad.net/kkubasik/ubuntu](http://ppa.launchpad.net/kkubasik/ubuntu)

I guess it came in from my Beagle experimentation, but the libbeagle 3.0 in there has some problem with Nautilus.
I marked the KKubasic repositary off deinstalled and reinstalled libbeaglo (2.8 Ubuntu) original and all works fine now.

Cheers
'
Palmer

---

### Post by jimbo99 on 2007-12-29
Let's just say that this is an incredibly nasty problem.  It has the potential of KILLing every single Ubuntu installation on the planet.  I think there's a need to have significantly TIGHTER controls to lock down to ensure there are no experimental versions that get into the installed base.

This is serious.  This is incredibly serious.  You can totally destroy everyone's Ubuntu with a mistake like this.  My whole desktop became unusable.  I had to use various tricks.

Beagle shouldn't even be in the OS and it certainly shouldn't be tied to nautilus.  You want to get your jollies and make a search routine then untie it from nautilus.  You screw up everything because those that deside to remove beagle will also remove some other important files.

Just be smart and untie it.  Remove the dependencies.  Make it a completely stand alone product.  And stop crippling our workstations.

---

### Post by dbera on 2007-12-29
> **jimbo99 said:**
> Let's just say that **this** is an incredibly nasty problem.  **It** has the potential of KILLing every single Ubuntu installation on the planet.  I think there's a need to have significantly TIGHTER controls to lock down to ensure there are no experimental versions that get into the installed base.

I am not sure what are you referring to as the nasty problem above (bolded in the quote) ? All I understand is that some users installed beagle from a non-official repository and faced trouble. When they reverted back to the official ubuntu supplied package, everything was ok.

---

