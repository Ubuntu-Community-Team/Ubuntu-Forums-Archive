---
title: "splash screen causes boot problems"
date: 2006-11-07
forum: General Help
---

### Post by petertc on 2006-11-07
I have found having the splash enabled in the grub menu list causes my machine to start in terminal mode tty1 to get to X i have to Ctrl+Alt+F7, once this is done i can login as normal. 

Removing the splash from the menu list means the machine will boot and go straight to X where you can login. 

I took me a while to cure this by searching on the forums finding the answer was more luck than judgment. 

Any one else had this issue?

This could be a real pain for some one trying Kubuntu for the first time as they may not know how to swap between the consuls. also you could not startx from tty1 because it was already running on tty7.

---

