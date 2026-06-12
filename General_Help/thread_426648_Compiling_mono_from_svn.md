---
title: "Compiling mono from svn"
date: 2007-04-28
forum: General Help
---

### Post by radiohead on 2007-04-28
Hi, I am not sure if this should go into Installation and Upgrades, or this place, so whatever.

I try compiling mono from svn and I continue to get the same error...

```

Cannot open assembly ../../../mcs/class/lib/default/mcs.exe.
make[4]: *** [TestDriver.dll] Error 2
make[4]: Leaving directory `/home/radiohead/monostuffs/mono/mono/mini'
make[3]: *** [check-am] Error 2
make[3]: Leaving directory `/home/radiohead/monostuffs/mono/mono/mini'
make[2]: *** [check] Error 2
make[2]: Leaving directory `/home/radiohead/monostuffs/mono/mono/mini'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory `/home/radiohead/monostuffs/mono/mono'
make: *** [check-recursive] Error 1

```

I am using the default ./autogen.sh
Any help is appreciated.

---

### Post by paparucino on 2007-04-29
> **radiohead said:**
> Hi, I am not sure if this should go into Installation and Upgrades, or this place, so whatever.

I try compiling mono from svn and I continue to get the same error...

```

Cannot open assembly ../../../mcs/class/lib/default/mcs.exe.
[code]

I am using the default ./autogen.sh
Any help is appreciated.

Try this

Then, go into the mono directory, and configure:
[CODE]
  $ cd mono
  $ ./autogen.sh [COLOR="Red"]--prefix=/usr/local[/COLOR]
  $ make
  $ make install

```




UAResolved

---

