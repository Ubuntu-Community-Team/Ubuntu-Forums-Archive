---
title: "Icons in &quot;Open With&quot; file menu"
date: 2012-10-27
forum: General Help
---

### Post by cogset on 2012-10-27
This easily is a really minor issue,however,if it can  be fixed,why not do it:I have some icons missing in the "Open With" right-click file menu,the one that can also be accessed via the Properties tab,in its place there is either a blank space or the generic blue diamond icon,the weird thing is that the very same programs in another Ubuntu Lucid installation (same version) do have those tiny  icons,so I was wondering if  it's probably something minor hidden in a configuration file.
I had a look in ~/.local/share/applications and for instance one of those applications has  a .desktop file with these lines 
```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec='/usr/sbin/xnview' %f
Name=xnview
Comment=Custom definition for xnview
NoDisplay=true
```is ,by any chance, this the file to edit to show that little missing icon?

---

### Post by cogset on 2012-10-27
Or am I completely off track,and this can be done (*if* it can be done) by means of some setting in gconf-editor ?

---

### Post by cogset on 2012-11-05
Just in case someone may wonder what I'm ranting about,I mean this tiny icon:in another Lucid installation I have the XnView icon instead of that generic one.

---

