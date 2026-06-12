---
title: "Installing tarball files from the GUI"
date: 2013-07-14
forum: General Help
---

### Post by Ifaistos on 2013-07-14
Hello :)

I just downloaded Komposer (WYSIWYG HTML editor) and I unzipped the file into a folder with the Archive Manager.

I was wondering if there is a way using a program from the GUI to install tarball files, or the unzipped version of the archive.

Does anyone know a way to install from apt-get the Komposer, or Bluegriffin software?

Thanks

---

### Post by Ifaistos on 2013-07-14
OK I am a bit dissappointed.
After a few hours of research.

There is not a single good WYSIWYG html editor for Ubuntu.

I ended up installing the Windows versions of Bluegriffin with Wine.
Which works great btw... :-)

If anyone knows a sure way that I can install with a .deb package Bluegriffin 64bit version for Raring, please let me know.

---

### Post by Ifaistos on 2013-07-14
oops.. sorry.. posted twice..

---

### Post by snowpine on 2013-07-14
You don't install "tarball" files. They are archive files (like .zip in Windows). So you extract them and see what is inside. :) 

Have you tried simply double-clicking on the "kompozer-bin" within your extracted folder?

Anyway, when you are talking about third-party software not provided or supported by Ubuntu, it is not Ubuntu's responsibility to provide clear, easy-to-follow install instructions---it is the responsibility of the third party providing the software. 

Here is a good intro to installing software in Ubuntu: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by monkeybrain2012 on 2013-07-14
As far as I know Komposer is no longer supported and it needs kde3 to work. If you are using KDE maybe you should use Kdevelop instead. Bluegriffin works natively in Linux btw, it is not in the repository but you get it by downloading a .deb from its website. To install the .deb just right click it (if you use Ubuntu rightclicking will bring up the Software centre which is slow, you should use gdebi for right clicking installers, but you need to install it first"sudo apt-get install gedebi", for KDE install gdebi-kde instead)

P.S. The Windows version of Bluegrifin apparently is bundled with crapware because the developer says he needs the money, don't know if it is still the case. But there is no crapware in the Linux version (I guess it makes no difference for Windows because the OS itself is a gigantic piece of crapware. :))so unless you like crapware there is no reason to use the Windows version in wine in your Linux box. :)

EDITED: Just checked. Bluegriffon comes not with a .deb but a tarball. There is no need for installation, just download it to your home, extract the tarball by right clicking and choose "extract here" or something to that extent depending on your de, then open the folder, and click the script "bluegriffon" to launch it, and that's it. If you like you can create a .desktop file for it (an icon which you click to launch the application)

---

### Post by monkeybrain2012 on 2013-07-14
Here is a simple .desktop file for bluegriffon

```
[Desktop Entry]
Type=Application
Name=Bluegriffon
Exec=/home/username/bluegriffon/bluegriffon
Icon=/home/username/bluegriffon/chrome/icons/default/default48.png
Terminal=false
Categories=Development;
```

Copy the text and place it in a text file and change the path /home/username/bluegriffon to where you have extracted the tarball. If you extract it to your home then just change 'username' to your own username. Then save the file as something like bluegriffon.desktop. Then right click it, and choose properties > permission and allow it to execute. Then move this to .local/share/applications and it will show up in the Unity dash or the menu, depending on your DE.

 .local is a hidden folder in your home so to see it you need to open the file manager, and then choose View > show hidden files or something like that depending on your DE, then you can just drop the .desktop file in there. Or from the terminal
```
cp pathtodesktopfile .local/share/applications
```

---

### Post by Ifaistos on 2013-07-15
Monkeybrain thank you for all your suggestions.
I do appreciate the time you took to help me out.

I had already done what you said in order to avoid the windows version.
I totally agree with you about windows, that is why I am "windows free" for years now ;-)

However the reason I couldn't run bluegriffon was because I could not run the script...  all I could was open it in gedit, and the .bin... does nothing when I open it or double click it...

I haven't started creating a desktop file because I couldn't run the software...

Any suggestions?

---

### Post by monkeybrain2012 on 2013-07-15
> However the reason I couldn't run bluegriffon was because I could not  run the script...  all I could was open it in gedit, and the .bin...  does nothing when I open it or double click it...

Open Nautilus, go to Edit > Preference > behaviour and look at the item Executable Text Files, I think you have the option "View" selected, you should select instead "Run" or "Ask". Also make sure the script is executable,--right click the script, choose Properties > Permission, check allow to execute.

---

### Post by Ifaistos on 2013-07-15
yeiiiii !!!!!

It worked :-)


Thank you so much :-)

---

