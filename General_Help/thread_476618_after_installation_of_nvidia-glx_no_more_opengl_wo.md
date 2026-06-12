---
title: "after installation of nvidia-glx no more opengl works"
date: 2007-06-17
forum: General Help
---

### Post by ehmdjii on 2007-06-17
hello, i did a fresh install of feisty and noticed that some opengl applications were not working because they complained that some extensions were not found. so i thought that maybe the nvidia drivers could make thins better and i did:

sudo apt-get install nvidia-glx

now unfortunately no opengl works at all. :(
when i type glxinfo

i get a bunch of error messages complaining about no extensions found.

how can i fix this or at least go back to my previous installation?

this is a geforce8600GT

thanks!

---

### Post by hardyn on 2007-06-17
you must install nvidia-glx-new.

if that board is even supported yet

---

