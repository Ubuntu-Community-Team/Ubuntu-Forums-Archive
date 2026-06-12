---
title: "How to change Main Menu Ubuntu Icon"
date: 2008-05-19
forum: General Help
---

### Post by Archel on 2008-05-19
I've tried to do it but it hasn't worked out for some reason. Anyone know how to do it?

Thanks.

---

### Post by Genius314 on 2008-05-19
Yeah.

Either:
A: Change "/usr/share/icons/Human/scalable/places/start-here.svg" as well as "/usr/share/icons/Human/NxN/places/start-here.png" (replace NxN with the size of your panel, such as 24x24. If you have an odd sized dock, such as 26 px, just change the svg in scalable). You need root privileges.
OR
B: Copy "/usr/share/icons/Human/" to "~/.icons/Human" and change the icons there, then just change the icon theme to the edited one in System>Preferences>Appearance.

Also, if you want to change a theme other than Human, just replace "Human" with the theme name. If you installed it yourself, you'll probably find it in "~/.icons"

Hope that makes sense. :)

EDIT: You said you tried it, but it didn't work, so I assume you know all that above. Just be sure to change the icon in scalable and the one in the folder for your dock size.

---

### Post by Archel on 2008-05-19
> **Genius314 said:**
> Yeah.

Either:
A: Change "/usr/share/icons/Human/scalable/places/start-here.svg" as well as "/usr/share/icons/Human/NxN/places/start-here.png" (replace NxN with the size of your panel, such as 24x24. If you have an odd sized dock, such as 26 px, just change the svg in scalable). You need root privileges.
OR
B: Copy "/usr/share/icons/Human/" to "~/.icons/Human" and change the icons there, then just change the icon theme to the edited one in System>Preferences>Appearance.

Also, if you want to change a theme other than Human, just replace "Human" with the theme name. If you installed it yourself, you'll probably find it in "~/.icons"

Hope that makes sense. :)

EDIT: You said you tried it, but it didn't work, so I assume you know all that above. Just be sure to change the icon in scalable and the one in the folder for your dock size.

I doesn't let me copy to the folder, I says I need privileges.

---

### Post by Genius314 on 2008-05-19
Well, you could copy the image in the terminal:

```
sudo cp /path/to/file1.svg /path/to/file2.svg
```

File1 should be the file you want to copy, file2 is the file you want to replace.

---

### Post by ajgreeny on 2008-05-19
Open up gconf-editor from terminal and navigate to apps>>panel>>objects and among the several numbered objects there should be one where the object type is "menu-object".  There are several others, one for each of the icons you have on the panel.

Using this "menu-object page" select the button "use_custom_icon" then in the line "custom_icon" right click, chose edit and add the path to your chosen icon.  If it's a png it doesn't matter too much about the size as it will fit to the panel.  Close the gconf-editor and when you reboot, the new icon should be there.

This is something I always do as I get rid of the upper panel and just use a single bottom one like KDE.  I have used an icon which I downloaded a long time ago, three colour versions of which I include as attachments.  I can't remember where I downloaded them but I like them a lot.  Feel free to use them if you like them also.

---

### Post by Genius314 on 2008-05-19
> Open up gconf-editor from terminal and navigate to apps>>panel>>objects and among the several numbered objects there should be one where the object type is "menu-object". There are several others, one for each of the icons you have on the panel.

Using this "menu-object page" select the button "use_custom_icon" then in the line "custom_icon" right click, chose edit and add the path to your chosen icon. If it's a png it doesn't matter too much about the size as it will fit to the panel. Close the gconf-editor and when you reboot, the new icon should be there.

Didn't know about that way. Thanks, that makes it much easier.
I also see a "menu_path" setting, which might also be very useful. :popcorn:

---

### Post by Archel on 2008-05-19
Haven't been able to do it. My bar is at 24 pixels and I'm using Clearlooks but I can't get it to work. I screwed and did everything on Human but I change over to Human icon set and I still don't see the icon I replaced it with.

---

### Post by adhika_rexuss on 2009-08-24
hi Archel, I think this [thread]("http://ubuntuforums.org/showthread.php?t=1214812") might be able to help you out.

---

