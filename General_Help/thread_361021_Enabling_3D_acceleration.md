---
title: "Enabling 3D acceleration??"
date: 2007-02-13
forum: General Help
---

### Post by coldopm on 2007-02-13
Your graphics card does not appear to be setup correctly.
Please check the documentation for your Linux distribution
and your graphics card drivers to ensure proper installation.

This is what I get when I run a test with Cedega. Can anyone tell me how to ensure my card is installed properly?

---

### Post by coldopm on 2007-02-13
If it helps at all I am using a PCI express 800, ATI

---

### Post by divague on 2007-02-13
i had a problem with the 3d test in cedega, what i did was to run it several time until it showed green the green square, and is working without problem.

---

### Post by Belboz99 on 2007-02-13
You need to be sure you're running ATI drivers.

I haven't used ATI on Linux much, so I am unsure whether the drivers included with Ubunutu offer 3D accleration.   You may need to install drivers from the universe or multiverse repositories.

If you want to verify that you do or do not have 3D acceleration, run this command in the terminal:

```

glxinfo | grep direct
```


Dan O.

---

### Post by Kubunteando on 2007-02-14
In the output of "glxinfo | grep -i render" , you should see the Direct Rendering says "Yes". Otherwise you don't have 3D HW acceleration enabled.

Try to check from here for the latest driver:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

I guess it is the Radeon Xpress 800.

Then download the ATI installer and follow this link to perform the installation:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2)

Then check again the "glxinfo | grep -i render".
When you get a "Yes" you are ready to go.

---

### Post by bvanaerde on 2007-02-14
You can always use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to install & configure the latest drivers.
It's really easy, and worked perfectly on both my laptop & desktop (both have an ATI card).

---

