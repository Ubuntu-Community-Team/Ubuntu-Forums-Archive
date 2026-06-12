---
title: "doesn't load, just restarts and restarts"
date: 2005-09-10
forum: General Help
---

### Post by tregetour on 2005-09-10
I tried to use the LiveCD on my HP pavillion desktop just now. It gets to "Uncompressing Linux .... OK Booting from Kernel" [or something to that effect] and then the computer restarts, plopping me back at the begining & getting me no where...
  Thank you for your brilliant ideas.

---

### Post by rafakl on 2005-09-10
Dont worry, its easy to resolve, i had the same problem:


when your cd loads and the ubunt logo appears, BEFORE you hit the enter key to start loading ubuntu write:

live acpi=off

and then hit the enter key  :razz: 

ubuntu must start loading  :)

---

### Post by tregetour on 2005-09-10
Thank you! that worked. Now I just need to figure out why it's only giving me 640x480 screen resolution ... but at least I have something to work with.

---

### Post by codejunkie on 2005-09-10
[QUOTE=tregetour]Thank you! that worked. Now I just need to figure out why it's only giving me 640x480 screen resolution ... but at least I have something to work with.[/QUOTE]
It's the onboard intel video driver i had the same problem on my hp desktop you need to change it from the intel one thats used on the live cd to vesa or update the intel driver you can do that and it works great if you install but you cant do that using the live cd i just thought that i'd let you know that it does work fine if you decide to install ubuntu on your desktop and that you won't be stuck with crappy resolution if you choose to install ubuntu it's a great OS.

---

### Post by rafakl on 2005-09-10
If you select live-expert at the start, you can choose the driver of your card.

Try "vesa" when the program ask you to select one, like codejunkie suggested.

---

### Post by tregetour on 2005-09-10
Thank you! I'm writing this using the LiveCD session. The great community support here has convinced me that I have nothing to fear by installing ubuntu, and I'll be doing just that later today [once I back up my data &c.] You folks are awsome.

---

