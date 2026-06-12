---
title: "creating desktop launcher?"
date: 2013-01-19
forum: General Help
---

### Post by oxf on 2013-01-19
How do I create a new desktop launcher shortcut in 12.04 / Gnome?
Case in point: Adobe reader. if I just drag it on to the desktop it not the proper icon but the basic file with the arrow in it. How do I create the proper nice looking Adobe logo shortcut?

Thanks...

---

### Post by slickymaster on 2013-01-19
First you need to install gnome-panel package using the following command from your terminal:
```
sudo apt-get install --no-install-recommends gnome-panel
```
Then create the new launcher:
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```
This will open the create laucher dialog box here you can give a suitable name for the launcher. In the Command field, type in the command to launch the application Then, click OK to create the desktop launcher.

---

### Post by mc4man on 2013-01-19
> **oxf said:**
> How do I create a new desktop launcher shortcut in 12.04 / Gnome?
Case in point: Adobe reader. if I just drag it on to the desktop it not the proper icon but the basic file with the arrow in it. How do I create the proper nice looking Adobe logo shortcut?

Thanks...
If you're referring to acroread (Adobe Reader) - 

Delete what you now have, then open a terminal
```
cp /opt/Adobe/Reader9/Resource/Support/AdobeReader.desktop ~/Desktop/

```

```
chmod u+x Desktop/AdobeReader.desktop
```

---

### Post by oxf on 2013-01-19
> **mc4man said:**
> If you're referring to acroread (Adobe Reader) - 

Delete what you now have, then open a terminal
```
cp /opt/Adobe/Reader9/Resource/Support/AdobeReader.desktop ~/Desktop/

``````
chmod u+x Desktop/AdobeReader.desktop
```


OK thanks that was remarkably simple!
What about Libraoffice Writer then? How do I substitute that in the above code? I wonder if this is covered in a tutorial anywhere?

Caitlin

---

### Post by oxf on 2013-01-19
No I guess I cant' LibraOffice is in /etc but I don't see how to do this

---

### Post by mc4man on 2013-01-19
> **oxf said:**
> No I guess I cant' LibraOffice is in /etc but I don't see how to do this
Basically the same thing for .desktops stored in non-standard places. So in this case - 
```
cp /usr/lib/libreoffice/share/xdg/writer.desktop ~/Desktop/

```
```
chmod u+x Desktop/writer.desktop
```

To show a bit more - 
In /usr/share/applications you'd find the "LibreOffice Writer" symlink.
So if you right click on it > properties you'd see "Link Target" which will show you where the actual .desktop is (launchers are .desktop files that are executable

In this case, screen 1, the path is truncated but easy to figure.
../../ mean 2 directories up (back), so that would be - 
/usr[COLOR="Red"]/share/applications[/COLOR], so /usr
Then then rest of the path is shown - 
/lib/libreoffice/share/xdg/writer.desktop
So then you'd know - 
/usr/lib/libreoffice/share/xdg/writer.desktop

If desired another way other then cli command would be to browse there in nautilus, (/usr/lib/libreoffice/share/xdg/),  > right click on "writer.desktop" > copy to > Desktop

Then just right click on the writer.desktop on your Desktop > properties > permissions > click once in the Execute box - screen 2

---

### Post by mc4man on 2013-01-19
To possibly also answer thread question generically - 

You could just create your own or as mentioned use alacarte - easy to create own.

A very basic min .desktop for an app launcher would be - blue needs to be filled in, Mimetype= is optional
(you can use any name you wish on the Name= line, same for icon though for some icons better to full path on the Icon= line
```
[Desktop Entry]
Version=1.0
[COLOR="Navy"]Name[/COLOR]=
[COLOR="Navy"]Icon=[/COLOR]
Type=Application
[COLOR="Navy"]Categories=[/COLOR]
[COLOR="Navy"]Exec=[/COLOR]
MimeType=
```

So for libreoffice writer - 

```
gedit ~/Desktop/writer1.desktop
```
```
[Desktop Entry]
Version=1.0
Name=LibreOffice Writer
Icon=libreoffice-writer
Type=Application
Categories=Office;
Exec=libreoffice --writer %U
MimeType=
```

If you wanted to be able to drag & drop supported files on to the launcher then add those mimes to the MimeType line, no spaces, it's one **Long **line though won't look quite that way in your text editor - screen

So using the full set  - 
```
[Desktop Entry]
Version=1.0
Name=LibreOffice Writer
Icon=libreoffice-writer
Type=Application
Categories=Office;
Exec=libreoffice --writer %U
MimeType=application/vnd.oasis.opendocument.text;application/vnd.oasis.opendocument.text-flat-xml;application/vnd.oasis.opendocument.text-template;application/vnd.oasis.opendocument.text-web;application/vnd.oasis.opendocument.text-master;application/vnd.sun.xml.writer;application/vnd.sun.xml.writer.template;application/vnd.sun.xml.writer.global;application/msword;application/vnd.ms-word;application/x-doc;application/x-hwp;application/rtf;text/rtf;application/vnd.wordperfect;application/wordperfect;application/vnd.lotus-wordpro;application/vnd.openxmlformats-officedocument.wordprocessingml.document;application/vnd.ms-word.document.macroenabled.12;application/vnd.openxmlformats-officedocument.wordprocessingml.template;application/vnd.ms-word.template.macroenabled.12;
```

Then make your launcher, (.desktop) executable

---

### Post by oxf on 2013-01-20
> **mc4man said:**
> To possibly also answer thread question generically - 

You could just create your own or as mentioned use alacarte - easy to create own.



Hi,

Thanks so much for the very detailed explanations above! Written in a way that I can digest and understand. I learnt something today :p

Thanks again
Caitlin

---

