---
title: "How can I use an appimage as a default?"
date: 2017-06-27
forum: General Help
---

### Post by xeddog on 2017-06-27
I have just started dipping my toes into 3D printing and one of the applications that seems to be _very_ popular is Cura.  I have downloaded the appimage and it works fine, and I have made a .desktop entry so I can run it from the Unity launcher.  But I still have a couple of issues, one minor and one not.

Minor - No icon seems to be available for the launcher.  I just get the grey "?".  I can deal with that but . . .
Major - I am unable to use it to open .stl files by default.  

Is there a way to define appimages to be used as default applications?


Thanks,

Wayne

---

### Post by mc4man on 2017-06-27
It's quite likely appimages aren't any different than any other installed app.
To set as default for a mime just right click on target file > Properties > Open With > and find your app in list. If not there - 

Assuming your .desktop file is in a typically located   applications folder (/usr/share/applications or /usr/local/share/applications or ~/.local/share/applications) open it in a text editor.

On the Exec= line add a space & %letter to the end of the line. %f %F %u %U are your choices & many times which you use isn't that important..
So for example  (gimp)
```
Exec=gimp-2.8 %U
```

Then check properties of an .stl file again.

---

### Post by CatKiller on 2017-06-27
> **xeddog said:**
> I have made a .desktop entry so I can run it from the Unity launcher. 

Minor - No icon seems to be available for the launcher.  I just get the grey "?".  I can deal with that but . . .


The icon that will be displayed is determined by the **Icon=** line in your .desktop file.

You can specify the full path if you want, but you don't need to if it's in a theme directory.

A simple way to do it would be to grab an image that you want to use for your icon and put it in ~/.local/share/icons/hicolor. Then put the name of the file on the Icon= line. You don't need to specify the extension. You may need to run ```
update-icon-caches ~/.local/share/icons/hicolor/
``` afterwards to get the icon updated.

---

### Post by xeddog on 2017-06-28
I knew I came to the right place.  Thanks guys.

For this desktop file the %f parameter was just the ticket.  That got me to the point where I could select it as the default program to open .stl files.  The next problem was Cura just doesn't like file names with spaces, so I had to fix those.

Then I went to the Cura website and they had icons for download.  I got the one I wanted, place it somewhere temporary for the time being, update the desktop file, and waalaa.  I'll move it to a more permanent location later.

Thanks again,

Wayne

---

### Post by CatKiller on 2017-06-28
[This page]("https://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#exec-variables") lists the meanings of the %f, %U, etc field codes. It's possible that one of the others may handle spaces in filenames better.

---

