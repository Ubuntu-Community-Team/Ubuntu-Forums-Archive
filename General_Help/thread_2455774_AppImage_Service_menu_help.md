---
title: "AppImage Service menu help"
date: 2020-12-27
forum: General Help
---

### Post by adec2 on 2020-12-27
Hi, 
I'm trying to create a service menu for KDE to extract an appimage by right clicking the appimage in dolphin
This is what i have:

[Desktop Entry]
Type=Service
ServiceTypes=KonqPopupMenu/Plugin
MimeType=application/x-iso9660-appimage;application/x-appimage;application/vnd.appimage;
Actions=ExtractFromAppImage;
X-KDE-Priority=TopLevel
Icon=appimage.png


[Desktop Action ExtractFromAppImage]
Name=Extract From AppImage
Icon=appimage.png
**Exec= --appimage-extract**

The part starred is where i am stuck. The prefix i have got but how do I invoke any appimage before the "--appimage-extract"?
I understand there are other tools but i just want to do it by inserting $program --appimage-extract
Would a script work better and invoke that in the exec line?

Thanks

Edit. Consider this close i managed to do it by adding:

konsole --hide-menubar -e "%f --appimage-extract"

to the exec line

---

