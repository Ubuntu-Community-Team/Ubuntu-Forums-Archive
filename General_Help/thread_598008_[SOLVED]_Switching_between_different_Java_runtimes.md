---
title: "[SOLVED] Switching between different Java runtimes"
date: 2007-10-30
forum: General Help
---

### Post by PmDematagoda on 2007-10-30
Does anyone know the command which you can use to switch between the Java runtimes? I remember it to be something like "java-config", but it seems to be wrong.

---

### Post by nowshining on 2007-10-31
sudo update-alternatives --config java

---

### Post by dcstar on 2007-10-31
> **nowshining said:**
> sudo update-alternatives --config java

Or install the **galternatives** package and you will have a GUI interface available to run to view or modify all those settings.         :cool:

---

### Post by PmDematagoda on 2007-10-31
Thank you nowshining, your command was exactly what I needed:). But thanks to dcstar for his good recommendation, the package is very useful:).

---

