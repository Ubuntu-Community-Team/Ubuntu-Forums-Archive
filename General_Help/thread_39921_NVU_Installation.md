---
title: "NVU Installation"
date: 2005-06-07
forum: General Help
---

### Post by omiazad on 2005-06-07
Let me tell you first that I'm very new in Linux World and Ubuntu is my first choice.

I have downloaded [color=Red]nvu-1.0PR-pc-linux2.6.10-gnu.tar.bz2[/color] and extruct that in  [color=Red]/home/omi/Downloads/nvu-1.0PR[/color] directory. From root command prompt I can start the application by typing ./nvu and it's working fine.

But I want to enable GTK and use it. Without GTK (or pango) enabled, I cannot see Bangla working perfectly.

Can anyone help me regarding this?

---

### Post by ruben_b on 2005-06-07
you can install nvu easy with synaptic as a deb-file.

just have a look at ubuntuguide.org for how to add backports repositories and how to install nvu ;)

---

### Post by omiazad on 2005-06-07
In [color=Red]http://ubuntuguide.org/#nvu[/color] way, can I get a NVU Pango/GTK enabled?

---

### Post by AgenT on 2005-06-07
[QUOTE=omiazad]In [color=Red]http://ubuntuguide.org/#nvu[/color] way, can I get a NVU Pango/GTK enabled?[/QUOTE]

Do you mean using apt-get from the regular Ubuntu repository? You may want to try installing the newer version from the Ubuntu Backports project.

If neither have what you want, that means you are going to have to compile the program yourself since it was compiled without those options (although maybe for good reason).

---

