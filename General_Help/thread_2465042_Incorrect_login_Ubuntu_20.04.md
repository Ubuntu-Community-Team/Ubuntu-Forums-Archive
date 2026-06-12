---
title: "Incorrect login Ubuntu 20.04"
date: 2021-07-20
forum: General Help
---

### Post by alonsosara44 on 2021-07-20
Hi!


I am  trying to boot Ubuntu Desktop in the Cortex-A53 cores (Arm64) of the Zynq Ultrascale+ ZCU102. I have downloaded the rootfs from here: [https://cdimage.ubuntu.com/releases/20.04/release/](https://cdimage.ubuntu.com/releases/20.04/release/) ([Raspberry Pi Generic (64-bit ARM) preinstalled server image]("https://cdimage.ubuntu.com/releases/20.04/release/ubuntu-20.04.2-preinstalled-server-arm64+raspi.img.xz")). Then I have created the BOOT.bin and image.ub with Petalinux and I have copied them and the rootfs in the SD card.


But when I boot and try to login I get the "Login incorrect" message. I have tried different usernames and passwords:
ubuntu login: root / Password: root
ubuntu login: ubuntu / Password: ubuntu
ubuntu login: ubuntu / Password: (empty)


I am not sure if the .img file I have downloaded from the link above is valid for the zynq too. If it is, does anyone know how can I login? If it is not, does anyone know where can I download the correct one?

---

