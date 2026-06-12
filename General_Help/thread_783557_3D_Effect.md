---
title: "3D Effect"
date: 2008-05-05
forum: General Help
---

### Post by nirmal.santhosh on 2008-05-05
I am having NVIDIA(R) GeForce(R) Go 6150 graphics driver in my laptop .Its not supporting the 3D Effect with ubuntu 8.04 but it is supporting with Vista .What I have do , can any please help me out.

Advance Thanks.... :KS

---

### Post by BluePlum on 2008-05-05
have you enabled restricted driver?

---

### Post by tommyhakinen on 2008-05-06
You need to enable the restricted driver. To check if you're having 3D direct rendering, simply type this in terminal. It will output if you have or not.

> glxinfo | grep 'direct rendering'

---

