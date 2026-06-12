---
title: "Nautilus eats all my RAM and swap and hangs my PC"
date: 2008-02-29
forum: General Help
---

### Post by amorangi on 2008-02-29
When Nautilus opens a folder that contains several thousand images it rapidly consumes all the RAM and all the swap. So much so that the only thing to work is the mouse cursor. No keyboard responses work, not even ctrl-alt-backspace. I wait and wait, but after an hour the only practical thing I can really do is a hard reboot. 
I'm now trying to use grsync to sync some directories, and this obviously uses Nautilus as well, as if a have a system monitor running I can watch the machine die as once again I observe Nautilus eating all the memory.
This has happened to me on several different machines/versions of Ubuntu, my current setup is 4GB/RAM 4GB/swap quad-core - why any program should feel the need to consume 8GB of virtual memory is beyond me!.
 
What I would like to know is 
a)is there a fix (turning off the thumbnails doesn't seem to help)? 

b)can I limit the amount of RAM Nautilus uses so it doesn't freeze my whole system and at least I can get the opportunity to kill it?

c)can I replace Nautilus as the default file manager (at this point I am so sick of Nautilus anything is better) so that programs like grsync won't use it when my back is turned?

---

### Post by kish on 2008-02-29
This helped me 

nautilus -q

it gives a clean desktop. 

No ideas about other things sorry:(

---

