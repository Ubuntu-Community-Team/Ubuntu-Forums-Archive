---
title: "gpaste problem"
date: 2016-09-28
forum: General Help
---

### Post by jgw on 2016-09-28
I was using diodon as a clipboard manager but, under 16.04 it doesn't work anymore and rather than fight it I went out and install gpaste.  There were two things to install so I installed them both.  I can get it up but the second thing said it was a gnome applet icon which I assumed I might be able to stick on the top bar.  Anyway, after getting them all installed I have absolutely no idea what to do with the applet and thought I would ask.

I went to the system monitor and it has two gpaste files running; gpaste-daemon and gpaste-ui

In the unity launcher I pinned GPaste which is represented with a question mark icon.  I also cannot figure out how to change that icon.  I have gone to the gpaste.desktop and took a look.  Here it is:
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=GPaste 3.18.3
Icon=/media/greg/b75f5404-a582-476c-8623-78bcbcbdbdc3/Icons/Clipboard-3-64.png
Path=/
Exec=/usr/lib/gpaste/gpaste/gpaste-ui --gapplication-service
StartupNotify=false
StartupWMClass=Gpaste-ui
OnlyShowIn=Unity;
X-UnityGenerated=true

The Icon= is pointed to the correct icon file.  I stuck that file in its own folder so I could get rid of it if its wrong.  This file was changed when I went to /usr/lib/gpaste/gpaste/ and changed the icons on every gpaste file there (there were 3 of these.  gpaste.ui, gpaste.applet, and gpaste.daemon   I have checked every gpaste file I could find and checked anything doing with icons.  All that being said the icon simply remains the question mark icon.  I should also mention that I have also restarted the system just to see if that made any difference - it didn't.

Thank you................

After much messing around I found that Unity replaced gnome and I think this is the problem.  I have moved on to CopyQ which seems to be just fine and gives me an icon on the top bar.  I think the problem is that gpaste is a gnome application and gnome has to be running to get the icon onto the top bar.  Could be wrong but I am moving on.

---

