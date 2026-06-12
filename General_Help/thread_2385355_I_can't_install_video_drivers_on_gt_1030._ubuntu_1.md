---
title: "I can't install video drivers on gt 1030. ubuntu 17.10"
date: 2018-02-19
forum: General Help
---

### Post by mikhail-gavrilec on 2018-02-19
Hello everyone. I tried to install video drivers with follow commands:
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo ubuntu-drivers autoinstall
sudo apt full-upgrade
sudo rebootbut when I make reboot 
it's cycling on the black monitor and white words.
please, help me

---

### Post by monkeybrain20122 on 2018-02-19
17.10 defaults to wayland where nvidia's driver don't work. You need to login to xorg to install the driver, maybe that is the reason?

---

### Post by mikhail-gavrilec on 2018-02-19
Thank you. I solved the problem booting from insecure mode.

---

