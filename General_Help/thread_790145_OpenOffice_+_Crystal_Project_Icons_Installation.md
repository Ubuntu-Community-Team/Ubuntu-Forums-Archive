---
title: "OpenOffice + Crystal Project Icons Installation"
date: 2008-05-11
forum: General Help
---

### Post by ibun2 on 2008-05-11
Would someone please tell me how to install the icons found here: [http://www.everaldo.com/crystal/?action=downloads](http://www.everaldo.com/crystal/?action=downloads) for OpenOffice? Thank you!

---

### Post by proffeszor on 2008-05-11
I think like always you should drag and drop the archieve into the themes window. It should ask if you would like to activate installed icons theme and thats all. 

Try this link [http://art.gnome.org/themes/icon/1150](http://art.gnome.org/themes/icon/1150)

If it doesnt work the same way, try google it.

P.S. you may have to restart your graphics for theme to take effect. simply ctrl+alt+backspase

GL

---

### Post by ibun2 on 2008-05-11
I'm asking for help installing the OpenOffice theme, not the system-wide icon theme. I'm on Kubuntu, but this applies to all -buntu variants.

---

### Post by ibun2 on 2008-05-13
Bump. Someone must know how to do this.:-\"

---

### Post by macaholic on 2008-05-13
If you do find out, let me know, I'm having my own OOo icon troubles aswell, see [here]("http://ubuntuforums.org/showthread.php?t=791023").

---

### Post by ibun2 on 2008-05-29
Bump. I found these instructions on KDE-Look

To install on OpenOffice 2.2.1 on Kubuntu Feisty 7.04:
- backup the file /usr/lib/openoffice/share/config/images_crystal.zip
- Download the crystal icons for OOo at [http://everaldo.com/crystal/crystal_project_OOO.zip](http://everaldo.com/crystal/crystal_project_OOO.zip)
- Unzip
- Enter the OOo folder created from the Unzip process
- Create a zip file with all folders and call the archive images_crystal.zip
- Copy that file (with root privileges) in the /usr/lib/openoffice/share/config/
- If you want to make them as default icons backup the /usr/lib/openoffice/share/config/images.zip and replace it with your archive
- Start OpenOffice
- Go to Tools -> Options -> View menu and select Crystal style

Can someone spoon-feed me as to how to do this?

---

### Post by XPuntu on 2008-11-01
Do you still need help with this? You're instructions worked fine for me. The only thing you need to do is start terminal and then do the unzipping, zipping and copying as root.

sudo nautilus

HTH

---

