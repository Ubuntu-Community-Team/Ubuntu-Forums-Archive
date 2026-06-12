---
title: "firefox scrolling lag"
date: 2008-05-11
forum: General Help
---

### Post by cuber351 on 2008-05-11
when scrolling in firefox with the mouse it will lag pretty badly
anyone know how i can fix this?

---

### Post by Endolith on 2008-05-11
Can you describe your system in more detail?  Is it Firefox 3 beta 5?  Ubuntu?  Does it scroll poorly on sites like Gmail, but works fine on other sites?

---

### Post by cuber351 on 2008-05-12
i tried firefox 2 and firefox 3, both have the same problem
it happens on all sites

1.89ghz processor
768mb ram

---

### Post by chorca on 2008-05-12
Do you happen to know what kind of video hardware you have in your system? Does the system lag when you move windows around on the screen, or only when you're scrolling in firefox?

---

### Post by cuber351 on 2008-05-12
64mb ati radeon 7500
only happens when scrolling in firefox in linux

---

### Post by chorca on 2008-05-12
Some other quick little tests:

1. Try playing back a video; any video will do, there's one in the Examples folder if you need one. See if it works at normal speed.

2. Try disabling Compiz desktop effects. They're turned on by default in Hardy, and can cause issues in certain rare cases. System Menu -> Preferences -> Appearance -> Visual Effects tab -> Select "None"

3. Have you installed the FGLRX driver? You shouldn't need it, hopefully X is using the radeon driver. Check to see if direct rendering is working by going into a terminal and typing 'glxinfo | grep direct' (without the apostrophies) If it says "Direct Rendering: No" then there might be a video card issue.

---

### Post by cuber351 on 2008-05-12
disabling the effects worked
is there a work around to this problem?

---

