---
title: "Cannot enable nouveau display driver"
date: 2018-03-08
forum: General Help
---

### Post by veer.exe on 2018-03-08
Hi ,
I have installed nvidia driver using below command.
./NVIDIA-Linux-x86_64-390.25.run --no-opengl-files --dkms


nvidia-settings gives error

[https://ubuntuforums.org/attachment.php?attachmentid=278851&d=1520514013&thumb=1&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=278851&d=1520514013&thumb=1&stc=1)


additional drivers does not allow to change Driver selection.

Query1 : how can I exectue nvidia-settings without error.
Query2: How can I enable Driver selection option in Aditional drivers.

I will be thankful for any reply.

---

### Post by ajgreeny on 2018-03-08
Which version of Ubuntu are you using and does it use xorg or wayland for the graphics?

The nvidia drivers are not yet usable with wayland as far as I'm aware, so if you're using 17.10 with wayland try logging in to xorg from the login screen.

---

### Post by monkeybrain20122 on 2018-03-08
You can install the Nvidia driver from the repository or the graphics-driver ppa [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) It is risky to do the ./run file route and you would have to manually recompile the driver each time you have a kernel update. I would uninstall whatever you have installed and remove everything Nvidia then reinstall the driver from the repository.

---

### Post by dorian7 on 2018-03-11
What is your graphics hardware?  Does this happen to be a dual hybrid/optimus graphic setup? In a laptop?

---

### Post by coffeecat on 2018-03-11
Support, not chat.

*Thread moved to **General Help**.*

---

