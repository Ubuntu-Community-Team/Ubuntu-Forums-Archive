---
title: "joy2Key in Dapper? Also, various upgrade issues (edgy)."
date: 2007-04-13
forum: General Help
---

### Post by GexX2 on 2007-04-13
There's no official package, so I was wondering how I'd accomplish this. I downloaded the edgy package and installed it, but it fails with 

```
Error opening /dev/js0!
Are you sure you have joystick support in your kernel?

```

And I don't have a /dev/js0 =.= Is there anyway to get joy2key to work in dapper? 

I can't upgrade to edgy due to my graphics card (nvidia 7800GT). I tried to upgrade to edgy and it completely destroyed X it would seem. And being an absolute Linux beginner  (want to learn :P) I reinstalled, as I have no clue how to reinstall x from terminal. Does anyone know of a workaround to the nvidia issue with edgy?

Also, my add/remove programs isn't updating correctly. It always says its out of date, and then when I reload it always downloads 28 new packages or whatever, and nothing changes. Before the reinstall, it had the abuse-sfx package listed, and now it doesn't no matter how many times I reload. Any help with that? Sorry for asking so much. I like Linux, but I'm pretty new to it, and I have no clue how to compile a source or whatever, and I'm kinda clueless on most of this stuff, so it would be appreciated.

---

### Post by wakingrufus on 2007-04-16
try:
 joy2key -dev /dev/input/js0

---

