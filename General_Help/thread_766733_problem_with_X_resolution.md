---
title: "problem with X resolution"
date: 2008-04-25
forum: General Help
---

### Post by InfoTech on 2008-04-25
After using "clone" option on TV I am experiencing problems with the resolution. After updating to 8.04, desktop environment is working fine, but there is still a problem with login screen: display is in smaller resolution than the screen, so I can only see 1/4 of the screen.

Any suggestions?
Thanks

---

### Post by InfoTech on 2008-04-26
Any ideas?
Thanks!

---

### Post by Zorael on 2008-04-26
Your TV will, of course, clone the content with the same resolution as displayed on your normal monitor.

Anyway, you can define the standard resolution in your /etc/X11/xorg.conf file. Once logged in, the login greeter reads *your personal* setting and applies it, but up until then, it doesn't know which user's setting to read from and as such, loads the default. That's likely what happens. (wrong standard, login, correct setting, desktop.) If there aren't any resolutions defined in said xorg.conf file, it'll default to the highest resolution your screen and videocard supports.

Make a backup of /etc/X11/xorg.conf, then open it up in an editor with superuser permissions (gksu gedit /etc/X11/xorg.conf). Scroll down to where it looks like this.
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Videocard"
    Monitor        "Configured Monitor"
    DefaultDepth    24
[b]    SubSection     "Display"
        Depth      24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600"
    EndSubSection[/b]
EndSection
```
The device names may vary, of course - just don't change them.

What you want to make sure of is that the "display" subsection is there, and that the resolutions you want to use are listed in the modes line. The *first* entry will be the default, so you likely don't want it to be 1600x1200 as in the example.

If that subsection isn't there at all, create it. Then restart X with Ctrl+Alt+Backspace and see if it worked.

---

### Post by InfoTech on 2008-04-28
Thanks! It helped! 

In addition, I found the following:

```
Virtual	1600	1200
```

Which I commented out as

```
#		Virtual	1600	1200
```

After that everything was just great!

Thanks again for your help!

---

