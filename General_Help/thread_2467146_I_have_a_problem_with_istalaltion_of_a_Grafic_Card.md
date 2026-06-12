---
title: "I have a problem with istalaltion of a Grafic Card amd hd radeon 7750"
date: 2021-09-16
forum: General Help
---

### Post by salbutamol2 on 2021-09-16
i cant complet a installation of a Radeon hc 7750 i have many error in the final line , i searched in youtube but  the videos dont have the problem , someone have a real steps for the instlallation
i used this comands

[https://amdgpu-install.readthedocs.io/en/latest/install-installing.html#installing-the-pro-variant](https://amdgpu-install.readthedocs.io/en/latest/install-installing.html#installing-the-pro-variant)
ty

---

### Post by QIII on 2021-09-16
amdgpu does not work with that GPU.

When Ubuntu is installed, the installer loads the correct module to drive the GPU.  In the case of AMD products, that is either the open source radeon module or the open source amdgpu module.  There is nothing more that needs to be done.

Attempting to install amdgpu with that GPU will result in either a module that has nothing to do or, worse, a machine that is inoperable.

If you were able to see anything on your monitor when you installed Ubuntu, then the correct driver module was loaded.

---

