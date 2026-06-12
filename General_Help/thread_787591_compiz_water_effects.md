---
title: "compiz water effects"
date: 2008-05-09
forum: General Help
---

### Post by kin9ofqu33nz on 2008-05-09
i enabled the watter effects..but nothing happens?...

---

### Post by NightwishFan on 2008-05-09
Did you activate them with shift+f9?

---

### Post by kin9ofqu33nz on 2008-05-10
yes i have..i even messed around with its settings..but NOTHING seems to work?

---

### Post by FuturePilot on 2008-05-10
What graphics card do you have? Some older cards don't have the necessary pixel shaders required for the water effects.

---

### Post by kin9ofqu33nz on 2008-05-10
i've got a Nvidia GeForce3 ti 200

---

### Post by FuturePilot on 2008-05-10
That's probably too old. I have a GeForce2 Go and the water effects don't work because it lacks the pixel shaders.

---

### Post by kin9ofqu33nz on 2008-05-10
oh r u sure?..cuzz everything else works fine..

---

### Post by FuturePilot on 2008-05-10
I'm pretty sure. You can check by running
```
glxinfo | grep GL_ARB_fragment
```
If it returns nothing, your card doesn't have the necessary pixel shaders.
But otherwise, everything else should work just fine.

---

### Post by kin9ofqu33nz on 2008-05-10
so on terminall all i do is type ...grep GL_ARB_fragment?..i did that..n nothin happened..

---

### Post by FuturePilot on 2008-05-10
You need to put the entire code in the terminal. You can copy and paste it if you want to.

---

### Post by kin9ofqu33nz on 2008-05-10
i did that..n nothin happened?

---

### Post by FuturePilot on 2008-05-10
Then your card doesn't have the pixel shaders needed for the water effects.

---

