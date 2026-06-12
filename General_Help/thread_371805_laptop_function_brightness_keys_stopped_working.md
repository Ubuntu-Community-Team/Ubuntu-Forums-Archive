---
title: "laptop function brightness keys stopped working"
date: 2007-02-27
forum: General Help
---

### Post by harty83 on 2007-02-27
For some reason my function brightness adjustment keys stopped working on my Compaq Presario V3000.  I just noticed it so I'm not for sure what could have caused it.  They work both in BIOS and in Windows xp but will not work in Ubuntu. 

Any clue what could have happened? I'm running Edgy with the latest updates.

Thanks!

---

### Post by harty83 on 2007-02-27
It seems that somehow things have gotten a bit remapped.  Fn-F8 now toggles my external monitor where Fn-F4 is suppose to do that. 

Before
  Fn-F4 - toggled monitor (although I don't think it worked originally)
  Fn-F7 - Decreased brightness
  Fn-F8 - Increased brightness

Now
  Fn-F4 does nothing
  Fn-F7 does nothing
  Fn-F8 toggles my monitor (I like this though because I've been wanting to be able to do this for a while, but I would rather have it work with fn-F4 like it is suppose to and the brightness keys work with f7/f8 like they are suppose to)

What would cause this switch??  I have not messed with my xorg file.

Thanks!
Alan

---

### Post by harty83 on 2007-02-28
I remembered that I did a bios upgrade.  So I downgraded and now my brightness keys work!

But my monitor export function key does not!!!!  Erg.

How does the monitor export key work?  Is it something that only BIOS can control?  If not, is there a manual way that I can tell my laptop to export to a monitor without screwing with dual monitor setups in xorg which I'm having one hell of a time getting to work (I've followed every tutorial I can find and none seem to work; I have an intel 945GM).

Thanks!

---

### Post by dannyboy79 on 2007-02-28
this happens to me sometimes on my Hitachi Visionbook Pro running Dapper Xubuntu. for some reason the brighter key won't work but the darker key will work. then the only way to get it to work again is to reboot. Obviously our situations are a little different but I wonder why this is happening?

---

