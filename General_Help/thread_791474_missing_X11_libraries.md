---
title: "missing X11 libraries"
date: 2008-05-12
forum: General Help
---

### Post by jorik42 on 2008-05-12
so, ive had this problem multiple times now; ive been trying to configure files pertaining to the setup/compilation of window managers, and when i run the configure command i have gotten the following error:

checking for X... no
configure: error: X11 libraries not found, so X11 package cannot be built


which seems to be odd to me as dont window managers require the X server to run???  So how is it that i dont have X...

i have the config.log file if that will help anyone; im not sure what to make of it.  

any help would be appreciated; i like trying new window managers and sometimes i cant find a .deb or a working apt-get method of getting them.  


jorik

---

### Post by chrisccoulson on 2008-05-12
Sounds like you have missing packages. Could you try
```
sudo apt-get install ubuntu-desktop ubuntu-standard ubuntu-minimal
```

This will make sure all the necessary meta-packages are installed on your system

---

### Post by jorik42 on 2008-05-12
i already had those installed, but i ran the apt-get command again; it updated and installed some new packages.  same error though when running the compile command.

---

### Post by chrisccoulson on 2008-05-12
Sorry, I misread your post. You're trying to compile stuff, so you need to make sure that the relevant '-dev' packages are installed for each of the dependencies that your source needs.

For X11:
```
sudo apt-get install libx11-dev
```
..or for all X related development headers:
```
sudo apt-get install xorg-dev
```

---

### Post by albertwt on 2010-11-14
> **chrisccoulson said:**
> Sorry, I misread your post. You're trying to compile stuff, so you need to make sure that the relevant '-dev' packages are installed for each of the dependencies that your source needs.

For X11:
```
sudo apt-get install libx11-dev
```
..or for all X related development headers:
```
sudo apt-get install xorg-dev
```

thanks for the reply man, if i need to install X Window libraries for the Ubuntu Server 64 bit 10.04 LTS is this the correct one to go ?

---

