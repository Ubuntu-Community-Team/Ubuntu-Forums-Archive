---
title: "No menu icon for application manually installed."
date: 2014-03-16
forum: General Help
---

### Post by cdysthe on 2014-03-16
Hi,

I have an application I had to install manually since it doesn't have an installer. I was told to put the 'application.desktop. file in /usr/share/applications and icons in the /usr/share/icons/hicolor 32x32, 16.16 and 128x128 folder. The images have the same name as the application. The application.desktop file looks like this:

[Desktop Entry]
Name=Application
GenericName=IM
Comment=Client for Groups
Exec=/opt/application/bin/application
Icon=application
Terminal=0
Type=Application
Encoding=UTF-8
Categories=Network;InstantMessaging;

The application shows up in the menu but without icon. Do I have to do some kind of refresh or something to get the icon to show? I did try to change the Icon= to another known application, and then it shows up, but with the correct icon it doesn't. Any ideas what I need to do to get this to work?

---

### Post by deadflowr on 2014-03-16
I would just use the full filepath to the icon.

**Icon=/usr/share/Icons/hicolor/32x32/iconnamehere.jpg**

or whatever it is.

---

