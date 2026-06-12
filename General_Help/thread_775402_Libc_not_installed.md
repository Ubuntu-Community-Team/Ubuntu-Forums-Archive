---
title: "Libc not installed"
date: 2008-04-30
forum: General Help
---

### Post by AdamMPkins on 2008-04-30
as i was attempting to install drivers for my nvidia graphics card, i was informed that i "have not yet installed libc." I was istructed to install libc and continue the installation. What is libc and how do i obtain it?

edit: to be specific, the error message says the following: "You do not appear to have libc header files instlled on your system.
Please instally your distribution's libc development package."

---

### Post by ryanhaigh on 2008-04-30
I am guessing that you are trying to install the drivers from nvidias website? If so this is not the recommended way of installing them as ubuntu provides the packages in their own repositories. 

To install go to system>admin>restricted driver manager. For more information have a look here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

This may also be useful to you: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Basically unless it is unavailable it is generally better to install using you Linux systems package management.

---

### Post by psoplayer on 2008-04-30
Nevertheless, if you want your original question answered, I believe all you need to do is install the build-essential package. To do so, open a terminal (Applications > Accessories > Terminal) and enter the following:
> sudo apt-get install build-essential
It will ask you for your password (and hide, any input from appearing), and will ask you to confirm your installation choice. Just enter 'y' and it will download and install everything you might need to compile software from source in the future. (The libc package should be included in this.)

---

