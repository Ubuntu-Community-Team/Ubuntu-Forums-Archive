---
title: "Install problem with Rapid Photo Downloader"
date: 2016-08-25
forum: General Help
---

### Post by flyingsolo on 2016-08-25
I'm on 16.04 and attempting to install latest version of RPD from [its download page]("http://www.damonlynch.net/rapid/download.html#installation").
Maybe I'm too green but when I click the Install Script link, I arrive at a page of comments and code but not sure what I do with it to run the script.
Pretty basic question I guess, but I'm stumped so far! A little help would be appreciated,
Thanks

---

### Post by CantankRus on 2016-08-25
Your browser is showing the script instead of downloading.
Use your web browser.. File > "save page as" menu to save as .py file to the same location as the **rapid-photo-downloader-0.9.0a4.tar.gz** archive.

After running the initial setup commands,
cd to the location of the downloaded files and run the install command given

---

### Post by dlynch3 on 2016-08-26
I have updated the download instructions to indicate the possible need to right-click on the links and choose the "Save Link As" option. Thanks.

---

### Post by CantankRus on 2016-08-26
Hello dlynch3,
Thanks for sharing your application and just to confirm for you (and flyingsolo)
**rapid-photo-downloader** installs and runs using your install guide on Xenial.

---

### Post by flyingsolo on 2016-08-26
Thanks to both CantanRus and dlynch3...So simple!
(first time I've run into that sort of browser issue)

---

### Post by flyingsolo on 2016-08-27
I'm not quite there with the install yet...
So, I ran the script as instructed and followed instructions for Ubuntu on the Download page, eventually running:

python3 install.py rapid-photo-downloader-0.9.0a4.tar.gz

as a regular (non sudo) user. It then asks for sudo priveleges during the install. All seemed to progress just fine but at the end, I can't seem to run the program.
FYI, I had the old version 0.4 from the U software center installed with a shortcut on the taskbar. Clicking it still launches the old version so I uninstalled the old version.
But still can't get the new to run. (no shortcut icon created; couldn't run from terminal)
What am I missing here?

---

### Post by howefield on 2016-08-27
> **flyingsolo said:**
> ...But still can't get the new to run. (no shortcut icon created; couldn't run from terminal)

I have just test installed the application in a 16.04 machine which worked as expected.

Did you logout and log back in as requested during the installation ?

```
Logout and login again to be able to run the program from the commmand line or application launcher
```

---

### Post by flyingsolo on 2016-08-27
Mea culpa!  I missed that *pearl*! (kind of equivalent to "Read the &%$ manual.") Many thanks and all is good now.

---

### Post by howefield on 2016-08-27
> **flyingsolo said:**
> Mea culpa!  I missed that *pearl*! (kind of equivalent to "Read the &%$ manual.") Many thanks and all is good now.

:)

I didn't mean it quite like that but it can be reasonably common that launcher icons don't show until you log out/back in. They are not usually so organised as to actually tell you that though as is the case here. Glad you got it going :)

---

### Post by dlynch3 on 2016-08-27
It's necessary to logout and login again because pip installs applications in ~/.local/bin, which is not a recognized application path on Debian/Ubuntu (unlike Fedora). However creating a link in ~/bin to the application in ~/.local/bin does work, thankfully. The login process in Debian/Ubuntu automatically detects the applications in ~/bin, ensuring they show in the menu.

I will probably update the installer script to ask the user if they want to uninstall version 0.4.x of Rapid Photo Downloader. I'll also consider highlighting some key messages from the installer script like the need to logout by making the terminal output bold or by placing them in a zenity or other GUI window.

I hope Alpha 5 will be out soon, with the main change being that file renaming configuration in the UI is finally implemented.

---

