---
title: "Ccsm broken - config problem?"
date: 2008-04-26
forum: General Help
---

### Post by jesusfreak180 on 2008-04-26
I had installed compiz-fusion from git before i upgraded to hardy.
Now i removed that and installed compizconfig-settings-manager.

when i run it i get:

```
me@me-ubuntu-laptop:~/compiz/compizconfig-python$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: /usr/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsStringToEdges
```

Then a crash report will pop up.

Anyone have any idea? The only reference to this i found was at a Russian forum, and i don't speak Russian :P

---

### Post by Zorael on 2008-04-26
This is likely due to version inconsistencies which makes stuff not play nice. Find compiz packages in Synaptic and pick **complete removal**.
```
$ sudo apt-get autoremove --purge compiz* libcompiz* emerald* libemerald* libdeco*
```
Then reinstall.

---

### Post by jesusfreak180 on 2008-04-26
```
me@me-ubuntu-laptop:~/compiz/compizconfig-python$ sudo apt-get autoremove --purge compiz* libcompiz* emerald* libemerald* libdeco*
Could not locate any suitable fingerprints matched with available hardware.
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-python.pc

```

What now?

I guess synaptic.

Will do

---

