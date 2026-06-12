---
title: "LibreOffice version for 18.04 LTS Bionic"
date: 2019-09-16
forum: General Help
---

### Post by nought2 on 2019-09-16
My system was installed from ISO for 16.04 LTS and upgraded to 18.04 LTS. LibreOffice version 6.0.7.3 is installed. I assume it is the latest LO version supported by Canonical because my system is updated daily.

Recently I encountered a minor problem when creating a document using LO Writer. A scanned PDF image file was inserted into a Writer ODT file. When the ODT file with embedded PDF image was exported to PDF, the embedded PDF image was not visible. Workaround: save scanned image as jpeg, gif or png and then insert in any of those file formats was successful.

I sought help for the problem at the LO support forums. After being pointed in the direction of the workaround I was asked to submit a bug report for the initial problem. Files uploaded to the bugzilla report were examined by someone using LO 6.3.1.2 on Win. That person was unable to replicate problem on his/her system. He/she also noticed that in files I had submitted PDF image had mysteriously been embedded as PNG, not PDF. The bug did not occur on his/her system. He/she suggested something is not behaving in my Linux build of LO.

Would there be any advantage in updating to a later version of LO? Is it possible that doing so might cause problems with LO and or the OS installation?

---

### Post by Dennis N on 2019-09-17
You can install the snap version or download an appimage to get a newer version. The latest version in either format is 6.3.1.

I have an appimage that coexists with the repository version of Ubuntu 19.04. Libre Office has the appimages for download on their web site.

---

### Post by nought2 on 2019-09-17
That's interesting. I hadn't heard of AppImages before. Now I know that portable apps for linux exist, good news.

Download page for LO AppImages is here:
[https://www.libreoffice.org/download/appimage/](https://www.libreoffice.org/download/appimage/)

What is the difference between 'Fresh' and 'Still' AppImages for LO?

---

### Post by deadflowr on 2019-09-17
Fresh equals newest stable. The latest stable version with the latest features.
Still equals older stable. Doesn't have the latest features but has been well tested.
[https://ask.libreoffice.org/en/question/69448/what-is-the-difference-between-libreofficefresh-and-libreofficestill/#69465]("https://ask.libreoffice.org/en/question/69448/what-is-the-difference-between-libreofficefresh-and-libreofficestill/#69465")
Currently fresh should be 6.3.1 and still should be 6.2.7

---

### Post by nought2 on 2019-09-17
Thank you Dennis N and deadflowr. Your advice was very helpful.

I downloaded LO fresh std 6.3.1 AppImage. At first glance it looks pretty good.

---

### Post by Dennis N on 2019-09-17
I place all my appimages in ~/appimages. To have a program launcher for these they need to have a .desktop file - some appimages create their own .desktop file and provide an icon on first run (example: etcher). But for most, you need to create a launcher manually by creating the .desktop file in ~/.local/share/applications. Ubuntu will read these and use the information to make application menu entries. In Ubuntu, launchers also will appear in its overview screen. If no icon is available, you can probably find an .svg image using google image search.

---

### Post by cruzer001 on 2019-09-17
An .svg image is the better way to go, but .png will do.  Place the image in /usr/share/pixmaps and your .desktop file will auto detect it by just the image name, no path needed.

Ps
Keep copies, a point release can at times clean out these directories.

---

### Post by nought2 on 2019-09-19
Thanks Dennis N and cruzer001 for your comments on creating a launcher.

I'd already created a launcher for the LO appimage with my rough and ready beginner's skill-set. I had it located in ~/Desktop, and for that launcher I made an icon with an .svg image by cropping an image file snaffled from the web.

I created a new *.desktop launcher following your respective recommendations for the locations of the LO 6.3.1.2 AppImage and the icon image file. The new *.desktop launcher was created by copying the old *.desktop file to ~/.local/share/applications and the old launcher in ~/Desktop was disabled. The *.svg icon image I'd created was copied to /usr/share/pixmaps. New *desktop launcher was edited to suit new *.svg file location; image file-name was substituted for full path to image.

Result of these changes is that I can hit the super key and type in the couple of letters of my unique launcher name (which is LO-631) and it pulls up the LO launcher matched with the *.svg icon image I made. 

When the program is actually launched, the icon for the LO-631 that appears in the program launch bar where favourites can be pinned is the standard LibreOffice icon, not the one I created. I am guessing the LO appimage overrode my image and used its own.

Is there any way to force it to use the one I created to save confusion with the version of LO installed from Ubuntu repository?

After launching LO-631, if the standard LO icon that appears is pinned to favourites, at next launch of LO from the pinned icon the installed version of LO is launched, not the appimage. Can the launcher I made be pinned to favourites so I can be sure to launch the appimage instead of the installed version?

---

### Post by Dennis N on 2019-09-19
> When the program is actually launched, the icon for the LO-631 that appears in the program launch bar where favourites can be pinned is the standard LibreOffice icon, not the one I created. I am guessing the LO appimage overrode my image and used its own.

Is there any way to force it to use the one I created to save confusion with the version of LO installed from Ubuntu repository?

After launching LO-631, if the standard LO icon that appears is pinned to favourites, at next launch of LO from the pinned icon the installed version of LO is launched, not the appimage. Can the launcher I made be pinned to favourites so I can be sure to launch the appimage instead of the installed version? 

----------------------------------
I saw similar behavior on the Ubuntu Dock and Dash to Dock in Fedora. Does not affect other desktops - not LXQt in particular, where I also used an appimage. Once the appimage is launched, clicking the dock icon switches to the running appimage even though the tooltip indicates its for the regular LO, so that still works as expected. The problem is with the initial launch.

To help me launch the right version of L.O. Writer, I gave the appimage a different name in the .desktop file (Writer Appimage). In the applications menu, both the appimage and regular version appear (see screenshot) so I could start there to select. Or, in the overview, both also appear in searching and in the applications display. (Note: I normally only use L.O. Writer, and my custom .desktop file is only for that application).

That's all I've done. I don't know the reason we can't reliably pin the appimage to the dock!

---

### Post by mörgæs on 2019-09-19
> **nought2 said:**
> My system was installed from ISO for 16.04 LTS and upgraded to 18.04 LTS. LibreOffice version 6.0.7.3 is installed. I assume it is the latest LO version supported by Cannonical because my system is updated daily.

Wrong. It's the latest Libreoffice version for 18.04 but a fresh install of 19.04 would have given you 6.3.1 by default.

---

### Post by nought2 on 2019-09-19
> **Dennis N said:**
> I saw similar behavior on the Ubuntu Dock and Dash to Dock in Fedora... That's OK. I can get used to launching LO 6.3.1.2 from super key + LO. I've unpinned the launchers of LO v6.0.7.3 Writer, Calc and Impress to save confusion; a side benefit is that it's useful to have more room in the Dock to see the list of running programs.

> **Dennis N said:**
> (Note: I  normally only use L.O. Writer, and my custom .desktop file is only for  that application).

Are there appimages for the individual components of LO? Didn't see any after a quick search. If not, how did you make a launcher just for LO Writer component of the bundled LO appimage?

---

### Post by Dennis N on 2019-09-19
> Are there appimages for the individual components of LO? Didn't see any after a quick search. If not, how did you make a launcher just for LO Writer component of the bundled LO appimage?

The downloaded AppImage contains all the applications (Writer,Calc,Draw,Impress,Math) and there are separate .desktop files for each of these (for the Ubuntu repository versions) in /usr/share/applications.

I looked at /usr/share/applications/libreoffice-writer.desktop, removed all the non-English comments and names, modified the filename, the Name= and Exec= command, reduced the mime types to just the one for .odt files. I saved the result in ~/.local/share/applications. My resulting .desktop file:

```
dmn@Tyana:~/.local/share/applications$ cat lo-writer-appimage.desktop
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice-writer
Type=Application
Categories=Office;
Exec=/home/dmn/appimages/LibreOffice-6.1.5-x86_64.AppImage --writer %U
MimeType=application/vnd.oasis.opendocument.text;
Name=Writer AppImage
GenericName=Word Processor
StartupNotify=true
```

The %U allows you to use the right-click context menu on an .odt file to open it with Writer AppImage.

As to my version number, I'm deliberately not using the latest version because after the 6.1 series, a feature I want to have was removed.

You could make other .desktop files for the individual applications from the suite that you need, or to use the LibreOffice start page, I think you would modify /usr/share/applications/libreoffice-startcenter.desktop.

---

### Post by nought2 on 2019-09-21
Dennis N, that last tip was pure quality. Manipulating the installed LO's own launchers to get the same behaviour for LO AppImage components is very neat. Thank you for sharing it with me.

---

### Post by Dennis N on 2019-09-21
Thanks for the feedback. I'm glad you found the information useful. You may want to mark the thread as solved.

---

