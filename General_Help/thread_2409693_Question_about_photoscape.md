---
title: "Question about photoscape"
date: 2019-01-05
forum: General Help
---

### Post by spamanon on 2019-01-05
I needed an easy photo editor so I downloaded photoscape.  Why does it NOT show up when I right click an image, "Open with other" and search for it?  I have to go to Activities and search for photoscape then open it and open the image from within.  But I want to set it as the default image viewer yet it doesn't show up even when I search for other programs?

Also, is there a better, more active ubuntu forum?  This one seems very slow.

---

### Post by him610 on 2019-01-05
Photoscape is a Windows program. To run it from Ubuntu, you need to install Wine first then photoscape into the wine environment.

> is there a better, more active ubuntu forum?

Probably not. Ubuntu forums is staffed entirely by dedicated, knowledgeable volunteers. Many of them are experts in the forum topics they respond to. They do not work for Canonical, and they receive nothing except the satisfaction that maybe they have helped someone.

---

### Post by spamanon on 2019-01-05
Thank you him610.  Photoscape runs just fine when I launch it from the search under Activities, so that _isn't_ the problem.

The problem is I want it to be the default image viewer.  So when I open an image, it opens in photoscape.  But photoscape does not show up in the list of choices.  It is not listed when I search for it in the "Open with other application" dialog, and it is not listed under the "default applications" panel either.  I don't understand ***why*** it isn't listed as an option either.  I would like to know why, but more importantly I would like to know how to make it be the default application for opening images since the default image viewer does not allow things like cropping, light adjusting, etc.

[IMG]https://i.imgur.com/XKgGI4w.png[/IMG]

---

### Post by Holger_Gehrke on 2019-01-05
@him610: Actually Photoscape is available from the Software-App as a snap and that's probably how spamanon installed it. But you're right, it's a windows app. The snap contains both wine and the program.

@spamanon: I just tried the snap from the software app and found it basically unusable. Icons without text or tool tips, L-O-N-G loading times and the problem you already encountered make it basically useless. So I removed the snap, downloaded the (windows) installer for Photoscape, opened a terminal and entered 'wine ~/Downloads/PhotoScapeSetup_V3.7.exe'. The installer ran without any problems and even produced an item in the menu. That fixes the missing texts and loads a lot faster, but doesn't fix the problem of not being able to start it from the context menu of image files. What (normally) happens when you run a program that way is that you pass the filename as a parameter to the program, so I tried (again in a terminal) ' wine ~/.wine/drive_c/Program\ Files\ \(x86\)/PhotoScape/PhotoScape.exe ~/Bilder/Kanne.jpg'. Didn't work. I don't know whether Photoscape can be called from the context menu in windows (haven't tried that ...), but unless there's some switch or option to pass in an image and start the editor or viewer directly, I don't know how to do it. Just posting this to document what I've tried, so somebody else can take over from this point.

Holger

---

### Post by again? on 2019-01-05
To be able to set photoscope as the default application, add %F to it's desktop launcher's "Exec" line.
I don't use snaps or wine but on my test partition I installed the photoscope snap package.

Then located the desktop file with...
```
locate photoscope.desktop
```

It showed a couple of files.
Files in /snap weren't writable.
Edited this desktop file....
```
sudo nano /var/lib/snapd/desktop/applications/photoscape_photoscape.desktop
```

Adding %F to the end of the "Exec" line. (so it's a space then %F)

If you're unfamiliar with nano, use arrow keys to navigate.
To save, press and release ctrl+x, then confirm with y followed by Enter.
[ATTACH=CONFIG]282107[/ATTACH]

Now in your file manager right click on a photo and choose properties > open with
Photoscape should show in applications list.
[ATTACH=CONFIG]282106[/ATTACH]


P.S.
It also works to copy the original launcher to ~/.local/share/applications and edit the copied launcher.
User launchers override system launchers and don't need root to edit and will not be over written with application updates.
```
cp /var/lib/snapd/desktop/applications/photoscape_photoscape.desktop ~/.local/share/applications/
gedit ~/.local/share/applications/photoscape_photoscape.desktop
```

---

### Post by Impavidus on 2019-01-06
For me, the terminal is the centrepiece of the operating system. When I want to open file X using application Y, I type a command line to start Y with the right arguments to let it open X. Usually, the command is Y X. I like it that way as it's fast and most of the time I want to specify both file and application, as I don't have a fixed application for most file types. Sometimes I start the application from the menu and then use it to navigate to the file I want to open, but that's slower.

Many people, like you, are more filemanager oriented. You use the filemanager to find file X and click it. The filemanager determines the file type and looks up which .desktop file describes how to open these files. Then it uses information from the .desktop file to construct a command line (the same one I enter directly) and launches the application, which uses its command line arguments to find out what file it has to open, then opens it.

Your problem is probably that you haven't got an appropriate .desktop file for photoscape. guber2 explains in the post above how to create one.

---

