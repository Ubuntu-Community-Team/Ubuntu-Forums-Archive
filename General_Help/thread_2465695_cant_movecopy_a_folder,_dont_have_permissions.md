---
title: "cant move/copy a folder, dont have permissions"
date: 2021-08-08
forum: General Help
---

### Post by grahaml2 on 2021-08-08
How do i move or copy a GIMP plugin to the Gimp folder, when i try i get a do not have permissions message.
The plugin is in the Download folder, the plugin is resynthesizer-master and is unzipped. The destination path is /usr/share/gimp/2.0
If I'm going to have to use the Terminal then best to assume step by step instructions needed 

Tanks for any help you can give

---

### Post by monkeybrain20122 on 2021-08-08
The plugin should go to your gimp's configuration folder in your home rather than the file system. You don't need special permission for that. Open your file browser, press ctrl+h or in the menu choose show hidden file. Find  a folder call .config inside there is a subfolder called GIMP and inside you'll see something like 2.10 (that depends on your gimp version) inside there is a folder called "plug-ins" Just put your plugin inside.

If you don't see the GIMP subfolder just run gimp once, it will be created automatically.

---

### Post by grahaml2 on 2021-08-08
Thanks for pointing me in the right direction, I found the Gimp folder inside of home/snap/gimp, for me the path home/config does not contain a gimp folder - i'm assuming the home/snap/gimp folder is the same as the home/config/gimp.
home/snap/gimp contains 4 folders three of which have plugin folders ?
Its late and i'm ready for sleep, I'll experiment tomorrow

again, thanks

---

### Post by Impavidus on 2021-08-09
It will be in ~/.config/GIMP/. GIMP in capitals and a dot before config, indicating it's a hidden directory. The directory should be created automatically when you first run gimp. ~ is your home directory. I don't know if any of this changes when you use the snap version of gimp. I never tried, but I don't expect so.

---

### Post by Dennis N on 2021-08-09
> The plugin is in the Download folder, the plugin is resynthesizer-master and is unzipped.
Locations for GIMP files in the Snap version are not going to be the same as for the Ubuntu repository version. A Google search on your issue turns up this:
[How to install Resynthesizer Plugin in GIMP snap?]("https://askubuntu.com/questions/1072044/how-to-install-resynthesizer-plugin-in-gimp-snap")

---

