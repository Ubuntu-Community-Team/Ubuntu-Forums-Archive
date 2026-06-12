---
title: "cannot change default office application"
date: 2018-05-19
forum: General Help
---

### Post by mfox on 2018-05-19
In Ubuntu 18.04, I am trying out a proprietary Office application called FreeMaker Office 2018. But when I installed it, it took over as the default application, and attempting to change this through the Properties/Open with dialogue box has no effect. This box works OK if I uninstall FreeMaker Office, so I know that this app must to something to lock itself in as the default. I'm wondering if there is some other way to change the default setting for word, spreadsheet and presentation applications; perhaps through the command line?

---

### Post by nlee2 on 2018-05-19
Have you tried

Tools-->Options-->LibreOffice-->Paths

---

### Post by mfox on 2018-05-19
nlee2, I found the setting in LibreOffice that you are referring to, but I don't see any options in Paths to set the default application for a certain mime type.

---

### Post by nlee2 on 2018-05-19
Oh now I get it. Have you tried reinstalling LibreOffice to restore the mime types?

---

### Post by mfox on 2018-05-19
I just did, but it neither moved FreeOffice from being the default application, nor allowed me to change that default. It must be doing something nasty to lock out that option.

---

### Post by Irihapeti on 2018-05-19
This is a known issue with FreeOffice that's been around for a while: [http://forum.softmaker.com/viewtopic.php?f=260&t=15137](http://forum.softmaker.com/viewtopic.php?f=260&t=15137)

I get around it by running FreeOffice in a VM when I need it, but I realise that running VMs isn't possible for everyone.

---

### Post by nlee2 on 2018-05-19
I looked at the postinst script and the installer creates unregister and remove icon scripts in the mime folder.

Will you share the method used to install and uninstall FreeOffice 2018 (i.e. deb package, single user)?

---

### Post by mfox on 2018-05-20
> **Irihapeti said:**
> This is a known issue with FreeOffice that's been around for a while: [http://forum.softmaker.com/viewtopic.php?f=260&t=15137](http://forum.softmaker.com/viewtopic.php?f=260&t=15137)
....
Irihapeti, I checked your forum link and this seems to be a different issue focused on icons rather than locking the default application for opening a file. But maybe they're related?

> **nlee2 said:**
> I looked at the postinst script and the installer creates unregister and remove icon scripts in the mime folder.

Will you share the method used to install and uninstall FreeOffice 2018 (i.e. deb package, single user)?
Again, I'm not sure that the icon issue and the locking default issue are part of the same. The file I installed was a .deb file. I installed it once with Software Installer and another time with gdebi. The result was the same.

When I uninstalled the file using gdebi, the app was removed and the icons seemed to have disappeared as well.

---

### Post by mfox on 2018-05-20
I discovered that installing FreeOffice 2018 either generates a file ~/.local/share/applications/mimeapps.list or adds to it, and looking in that file, most of the entries are for FreeOffice 2018. Once I uninstalled FreeOffice, I removed that file, and it seemed to have no impact on my associations. Furthermore, changing the association of a file seemed to work without having the mimeapps.list file in my .local folder. What I then did was reinstall FreeOffice, and saw that it created this mimeapps.list file again in my .local folder. This time I removed it and tried changing default applications, but it still didn't work. So whatever this program is doing to lock in my default applications, it must be in another place.

---

### Post by nlee2 on 2018-05-20
~/.local/share/applications/mimeapps.list is used by def.pl to fix KDE bug.

Have you tried running  FreeOffice 2018 as a portable app?

After FreeOffice installation, what is the output of

ls -la targetpathofinstall/freeoffice2018/mime

---

### Post by mfox on 2018-05-20
Thanks for sticking with me on this, nlee2. I once again reinstalled FreeOffice 2018, but could not find the target path of freeoffice2018/mime. Not sure what you mean by a portable app. Does this refer to installing it somehow on a usb stick? If so, wouldn't I need to be running a distro on that stick before I could install it?

I'm not sure this is meaningful, but it adds to the strangeness. After I uninstalled the program, I typed "locate softmaker" in a terminal. It located this in ~/.softmaker. But when I look for this in my home folder, I can't find it, even with hidden files revealed. Nor does it show with the "ls -a" command in a terminal. How could this be?

---

### Post by #&amp;thj^% on 2018-05-20
I don't mean to add further confusion here but when i install freeoffice i point it to my Home Directory.
```
ls
Desktop    freeoffice2018   presentations18free  uninstall_smfreeoffice2018
Documents  Music            Public               Videos
Downloads  pia.sh           SoftMaker
Encfs      Pictures         Templates
encrypted  planmaker18free  textmaker18free

```
But that's just my preference.
And for the "freeoffice2018/mime" have you looked in:
```
.local/share/mime/packages/softmaker-freeoffice18.xml

```
Yours might be different as I compiled my "softmaker-freeoffice-931-amd64.tgz" install.

---

### Post by nlee2 on 2018-05-20
The path should be

/usr/bin/freeoffice2018/

You can verify this with FreeOffice installed by using 

which textmaker18free

FreeOffice can run in portable mode and only use one folder for config. Do this by copying /usr/bin/freeoffice2018/ to another location or USB. Create an empty portable.txt file in that folder and run textmaker18free from that folder.
[http://www.freeoffice.com/en/tips-and-tricks-portable-installation](http://www.freeoffice.com/en/tips-and-tricks-portable-installation)

---

### Post by mfox on 2018-05-20
nlee2, you were close, as the command pointed to /usr/bin/textmaker18free, but that file appears to be a script to run textmaker. And 1fallen, you were right as to where the mime file is; it's ~/.local/share/mime/packages/softmaker-freeoffice18.xml. Before installing, I found another file like it in that location: ~/.local/share/mime/packages/softmaker-office-2018.xml. I removed it, installed, tried to change the default app preference and couldn't. So I then removed the file that was installed there (.../softmaker-freeoffice18.xml). Didn't matter, I still couldn't change the default opening program to any of the other programs I have. This FreeOffice is one tough cookie when it's installed.

---

### Post by #&amp;thj^% on 2018-05-20
have a look here: "/usr/share/applications/defaults.list"
Anything for freeoffice or softmaker

---

### Post by mfox on 2018-05-20
Yes; there are quite a few, and this is after the program was ininstalled. Here are some examples:

application/vnd.sun.xml.writer=textmaker-free18.desktop;libreoffice-writer.desktop
application/x-excel=planmaker-free18.desktop;libreoffice-calc.desktop
application/x-msexcel=planmaker-free18.desktop;libreoffice-calc.desktop
application/x-sylk=planmaker-free18.desktop;libreoffice-calc.desktop
application/xls=planmaker-free18.desktop;libreoffice-calc.desktop
text/rtf=textmaker-free18.desktop;libreoffice-writer.desktop
text/spreadsheet=planmaker-free18.desktop;libreoffice-calc.desktop

Could this be the problem? They shouldn't be there after I uninstalled the program.

---

### Post by #&amp;thj^% on 2018-05-20
Bingo! If your sure they or it was uninstalled you could change them back to Libreoffice>>
replace all occurrences of &#8220;libreoffice&#8221; or what ever you want replaced with &#8220;your chosen app&#8221;.
(Search &#8594; Replace &#8594; Replace All)

Finally, save the file. No need to restart, you&#8217;re all set!

---

### Post by mfox on 2018-05-20
Maybe I wasn't clear and my last post might have been misleading. After an uninstall, everything goes back to normal and I can choose what app I want as default. It's only after I install that the default app gets locked up to freeoffice. So it's interesting that after an uninstall that these references to freeoffice are still there, but they aren't affecting my ability to choose a default app.

---

### Post by #&amp;thj^% on 2018-05-20
Right then it's clear now. if your happy then I'm happy.
I have no problems with defaults installing freeoffice by hand to my Home directory. (Just Noting is all)
So I'm assuming your good to go now.

---

### Post by nlee2 on 2018-05-20
It was simpler for me to setup my own testbed rather than doing it blindly with just the postinst script in the deb. I did a fresh install of ubuntu 18.04 without LibreOffice. 

dpkg -i softmaker-freeoffice-2018_931-01_amd64.deb
install LibreOffice from Software Center

Doing it this way, the LibreOffice icons and mime types were maintained.

The install folder for FreeOffice is /usr/share/freeoffice2018. You can copy this folder to /usr/share/Myfreeoffice2018 and create portable.txt in it to run in portable mode after uninstall.

The scripts to unregister FreeOffice mime types and remove FreeOffice icons are

/usr/share/freeoffice2018/mime/unregister_smfreeoffice2018

/usr/share/freeoffice2018/mime/remove_icons.sh

---

