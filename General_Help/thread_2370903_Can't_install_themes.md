---
title: "Can't install themes"
date: 2017-09-08
forum: General Help
---

### Post by mrgnome on 2017-09-08
I'm trying to install the Azure theme from GNOME Look, but there's a problem. No matter what I do, I can't get the theme to show up in the Tweak Tool. I tried installing the theme with the OCS Desktop app, downloading the file from GNOME Look and extracting it to the .themes directory (which is what OCS did anyway). I also have the problem with cursors. How can I fix this?

---

### Post by Frogs Hair on 2017-09-08
Open the folder and once extracted you'll find a number of sub-folders with variations of the theme and these are folders used for installing the themes. After installed try logging out and back in and check for the new themes.

---

### Post by deadflowr on 2017-09-08
I'm guessing you're running this theme in particular:
[https://www.gnome-look.org/content/show.php/Azure?content=168843]("https://www.gnome-look.org/content/show.php/Azure?content=168843")

IF so double check to make sure you have the needed engine packages installed.
Simply run
```
sudo apt-get install gtk2-engines-murrine gtk2-engines-pixbuf
```

There's also an install file for it.
to run the install file
```
cd /themes/Azure-theme
./install.sh
```
if it gives a permission denied, do
```
chmod +x install.sh
```
and try the ./install.sh command again.

If, however, this is another azure theme, then ignore all I've posted.

---

