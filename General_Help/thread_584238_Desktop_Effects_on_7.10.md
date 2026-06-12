---
title: "Desktop Effects on 7.10"
date: 2007-10-20
forum: General Help
---

### Post by APMT19 on 2007-10-20
How do I get desktop effects on UBUNTU 7.10?

---

### Post by ihcnet on 2007-10-20
System -> Preferences -> Appearance Preferences -> Visual Effects Tab

---

### Post by UK-Wobbie on 2007-10-20
> **APMT19 said:**
> How do I get desktop effects on UBUNTU 7.10?

Do you have a graphic driver? Ubuntu needs one for 3D effects.

---

### Post by APMT19 on 2007-10-20
It says " The composite Extension is not availible" What do I do?

---

### Post by dcstar on 2007-10-20
> **APMT19 said:**
> How do I get desktop effects on UBUNTU 7.10?

Install the **compizconfig-settings-manage** package, then you will have it in:

System-Preferences-Advanced Desktop Settings

---

### Post by dcstar on 2007-10-20
> **APMT19 said:**
> It says " The composite Extension is not availible" What do I do?

What is your video hardware?

---

### Post by APMT19 on 2007-10-20
I have an ATI Radeon Mobility X700

---

### Post by misfitpierce on 2007-10-20
sudo apt-get install xserver-xgl

logout and in.... Note this uses XGL which may make things like videos either look worse or respond slow. ATI will release new graphics driver supporting AIGLX to run effects without XGL... when this comes out just simply remove XGL with sudo apt-get remove xserver-xgl

Have fun... :)

---

### Post by APMT19 on 2007-10-20
Why did it work in 7.04?

---

### Post by ihcnet on 2007-10-20
You probably used XGL in Feisty as well or you used the ati driver instead of the fglrx one.

---

