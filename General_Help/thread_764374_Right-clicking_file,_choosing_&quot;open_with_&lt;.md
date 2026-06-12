---
title: "Right-clicking file, choosing &quot;open with &lt;program&gt;&quot;, but program doesn't open file..."
date: 2008-04-23
forum: General Help
---

### Post by caljohnsmith on 2008-04-23
When I right-click on a media file, I have it set up so I can choose "Open with MediaInfo". The MediaInfo desktop file in my ~/.local/share/applications folder looks like this:

```
[Desktop Entry]
Encoding=UTF-8
Exec=/usr/bin/mediainfo_gui %f
Hidden=true
Icon=/usr/share/icons/hicolor/scalable/apps/ccsm.svg
MimeType=application/x-flash-video;
Name=MediaInfo
NoDisplay=true
Terminal=false
Type=Application
```

The problem is, when I right-click a media file and choose to open it with MediaInfo, MediaInfo opens, but it does not open the file I selected. So is this a problem with the "Exec=/usr/bin/mediainfo_gui %f" line above--should it be using something other than %f to send mediainfo_gui the correct file path to the file I clicked on? :confused:

In addition to getting a solution to this particular problem, is there someone who could point me to a good tutorial about variables like the %f above and how to use them when executing programs? 

Any help would be greatly appreciated! :)

---

### Post by ibuclaw on 2008-04-24
[QUOTE=caljohnsmith]
[Desktop Entry]
Encoding=UTF-8
Exec=/usr/bin/mediainfo_gui %f
Hidden=true
Icon=/usr/share/icons/hicolor/scalable/apps/ccsm.svg
MimeType=application/x-flash-video;
Name=MediaInfo
NoDisplay=true
Terminal=false
Type=Application
[/QUOTE]

try replacing "**%f**" with "**%s**".
Although it should make no difference.

Have you tried running it in the terminal launcher?
Hit **Alt+F2**, then type in:
```
mediainfo_gui **/path/to/file**
```
Regards
Iain

---

### Post by caljohnsmith on 2008-04-24
**tinivole:** I completely forgot about checking the program with a file at the command line since I (wrongly) assumed it worked, but that seems to be where the problem is. When I type "mediainfo_gui <file>" and give the full path to my file, it doesn't work. So it seems to be a problem with the program, not the %f parameter in the desktop file. If anybody else happens to know how to fix mediainfo, please let me know. :)

But just so I can understand it, what are the %f and %s parameters? And do they have the same meaning for every program? Thanks for any help!

---

### Post by mc4man on 2008-04-24
here is some info on .desktops
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.1.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.1.html)
or spec-1.0 for older

edit: where did you get a gui version for linux?

---

### Post by caljohnsmith on 2008-04-24
> **mc4man said:**
> here is some info on .desktops
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.1.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.1.html)
or spec-1.0 for older

edit: where did you get a gui version for linux?

Thanks for the link, mc4man, it's very helpful; I notice they don't mention %s. Where did you get %s, Tinivole? 

BTW, I got the GUI version of MediaInfo from their home at sourceforge:
[http://sourceforge.net/project/showfiles.php?group_id=86862](http://sourceforge.net/project/showfiles.php?group_id=86862)

I installed the .deb version, but maybe this is why it doesn't seem to work when passing files to it as arguments. Or maybe the program simply won't accept files as arguments from the command line in the first place? I'm not sure because it didn't come with a "man" entry. Would it maybe be better to download the generic linux version and go through the "configure" and "make" routine? I try to avoid that when I can because I usually run into problems getting programs to configure/make correctly.

---

### Post by mc4man on 2008-04-24
doesn't seem to be able to open file automatically, tried alot of combo's
the .desktop seems to have no use - editing or even deleting it has no effect
neither does the libmediainfo.so.0.0.0

---

