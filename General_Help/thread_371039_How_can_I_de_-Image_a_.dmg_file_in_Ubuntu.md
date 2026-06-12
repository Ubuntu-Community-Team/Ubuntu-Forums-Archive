---
title: "How can I de -Image a .dmg file in Ubuntu?"
date: 2007-02-26
forum: General Help
---

### Post by thenetduck on 2007-02-26
hi, 
 I have a file that has some music my friend made on his apple computer. He imaged the files together in a .dmg file to send it to me. I can't figure out how to de-image the .dmg file. Does anyone know a correct way to do this in Ubuntu? Thanks,

 The Net Duck

---

### Post by jdong on 2007-02-26
[http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

Basically you need to mount it loopback to some location. It's basically an HFS partition in a file, just like how a .iso is stored on the hard disk.

---

