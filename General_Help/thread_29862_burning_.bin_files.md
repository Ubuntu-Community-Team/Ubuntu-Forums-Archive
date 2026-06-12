---
title: "burning .bin files?"
date: 2005-04-26
forum: General Help
---

### Post by mitch2891 on 2005-04-26
Been using ubuntu for 4 days now and it is great but how do I burn .bin/.cue files?

What program do I use?

Please help

Thanks

---

### Post by cdhotfire on 2005-04-26
hmm, dont know if gnomebaker does it, but you could give it a try.
```

$ sudo gedit /etc/apt/sources.list

```
add
deb [http://backports.ubuntuforums.org/backports]("http://backports.ubuntuforums.org/backports") hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports]("http://backports.ubuntuforums.org/backports") hoary-extras main universe multiverse restricted

then
```

$ sudo apt-get update
$ sudo apt-get install gnomebaker

```

then just go to Applications -> Accessories -> GnomeBaker CD/DVD Creator

and try to do Burn Image.

If not you could use k3b, wish is guarranteed to work.:)
```

$ sudo apt-get install k3b
$ sudo apt-get install cdrdao

```

good luck. :)

Edit: make sure you dont open k3b with sudo or su, if not your gonna be in some trouble.:wink:

---

