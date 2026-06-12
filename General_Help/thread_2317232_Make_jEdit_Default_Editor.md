---
title: "Make jEdit Default Editor"
date: 2016-03-14
forum: General Help
---

### Post by box02-0 on 2016-03-14
Ubuntu 14.04 LTS. 64Bit                                                                         March.14.2016
Kernel 3.13.0
Unity 7.2.6       
NEMO 1.8.4


I am unable to assign jEdit to open text files.

This started when I upgraded jEdit from Rev 5.1.0 to rev 5.3.0 using the following steps:

1. REMOVED the old rev of jEdit 5.1.0 VIA Synaptic.
2.Downloaded  jedit5.3.0install.jar  from the jEdit website.
3. Installed the new rev:    java -jar  jedit5.3.0install.jar
 (I used the default directories)

    Program in: /home/mg/jEdit/5.3.0  
    Shortcut in: /home/mg/bin
    Manual in:/media/mg/Temp/Ubuntu DOC

Once installed, the new rev of jEdit runs aok.


Note: Synaptic will only re-install the old rev.


Currently the default “open” Application for text files is Geany, but I prefer to use jEdit. When I right click on any .txt file, Nemo gives me the option to “open” with a few Recommended Applications, along with allowing me to choose “Other Applications”. The problem: jEdit does NOT show up in the list. (I don't know if this is a Permissions issue?) 


The File /.local/share/applications/jedit.desktop contains the following:

[Desktop Entry]
Name=jEdit
GenericName=Programmer's Text Editor
Comment=Edit text files
Exec=jedit %F
Icon=jedit
Terminal=false
Type=Application
Categories=Development;TextEditor;
StartupNotify=true
MimeType=text/plain;
StartupWMClass=org-gjt-sp-jedit-jEdit
Keywords=Code;Editor;Programming;PHP;FTP;
Hidden=true


How do I get jEdit on the “open” Applications List for text files?

Thanks,


M….

---

### Post by QDR06VV9 on 2016-03-14
You also can add a custom command and to call it just enter this as the command &#8220;jedit" without the quotes..
More info here on JEdit: [http://www.jedit.org/FAQ/problems.html](http://www.jedit.org/FAQ/problems.html)

---

### Post by mc4man on 2016-03-14
Have you tried adding jedit.desktop to mimeapps.list for text/plain= 
(- [Added Associations] lines end with ;  [Default Applications] lines don't
Also to ck. run this & see if your jedit.desktop file  is any good
gtk-launch jedit

---

### Post by box02-0 on 2016-03-16
Hi.

Thanks for your prompt replies.


*“You also can add a custom command ...”*
Where would this custom command go?




[I]Have you tried adding jedit.desktop to mimeapps.list for text/plain=
(- [Added Associations] lines end with ; [Default Applications] lines don't
Also to ck. run this & see if your jedit.desktop file is any good
gtk-launch jedit [/I]


There is a mimeapps.list in:
/root/.local/share/applications/, and there is a:

    text/plain=jedit.desktop in the Default Applications


In /root/.local/share/applications/  there is a file called jEdit which is actually jedit.desktop when I try to open it with Geany. Don't really understand why the entry doesn't reflect the actual name of the file. In any event, when I click on this, jEdit works just fine.

When I go into Terminal, I can enter “jedit” and it launches just fine.

So how do I get jedit to be one of the “Recommended Applications”. Where is the list of “Recommended Applications” or “Other Applications” coming from?



Thanks,

M....

---

### Post by mc4man on 2016-03-16
Do you really mean the red? >  in [COLOR="#FF0000"]/root[/COLOR]/.local/share/applications/ there is a file called jEdit which is actually jedit.desktop

---

### Post by box02-0 on 2016-03-17
Sorry, meant [COLOR=#FF0000]home/[/COLOR].local/share/applications/ 

Thanks,

M...

---

### Post by mc4man on 2016-03-17
Atm using 16.04 which uses 5.3.0 so nothing to see there plus I use nautilus..
Why are you using Hidden=true in the .desktop? Maybe try removing, log out/in & see.

What also *may* be possible is to try installing the [16.04 package]("http://packages.ubuntu.com/fi/xenial/jedit") of jEdit, seems to only have some generic deps. (you'd need to remove current one first
Or try using it's .desktop  - 
```
[Desktop Entry]
Name=jEdit
GenericName=Programmer's Text Editor
GenericName[ca]=Editor de text per a programadors
GenericName[cs]=Textový editor pro programátory
GenericName[de]=Texteditor für Programmierer
GenericName[es]=Editor de textos para programadores
Comment=Edit text files
Comment[ca]=Editeu fitxers de text
Comment[cs]=Edituje textové soubory
Comment[de]=Editiere Textdateien
Comment[es]=Modifique archivos de texto
Exec=jedit %U
Icon=jedit
Terminal=false
Type=Application
Categories=Development;TextEditor;
StartupNotify=true
MimeType=text/plain;
StartupWMClass=jedit
Keywords=Code;Editor;Programming;PHP;FTP;
```

To answer earlier question,
All .desktop's have a file name, this cannot be changed after orig creation. (can be appended to which is worthless.
The display name of a .desktop is whatever is on the Name= line, this can be altered at will.

---

### Post by QDR06VV9 on 2016-03-17
You can also just right click on a text file and scroll down the dropbox and click on Open With and you will see the window with installed Apps but Down at the bottom you will also see a **+Add button** click that and another window pops up and at the bottom of that you should see an option to add **"Use a custom command" **Click the +(Plus or Add) and in that field just enter "jedit" with out the quotes...and now you have the jedit option as default for that sort of file.
Screenshot included..

You also can add that to your menu by editing your menu options.[s] Don't know what Desktop you are currently using or I would have better instructions for you.[/s]
<Snip>
For Unity For Ubuntu 15.10 or 14.04 LTS (11.10 or later, with Unity (3D))
[http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand](http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand)  Post by david 6

NOTE: This can replace the function of an existing icon, or (once created) can be searched for (from Dash icon) to add to current button-bar.
Hope this is helpful.

---

### Post by box02-0 on 2016-03-21
Hi.


*mc4man: Why are you using Hidden=true in the .desktop? Maybe try removing, log out/in & see.*


Problem is resolved. It was all about Hidden=true. As per mc4man I removed that line in:    [SIZE=2]/.local/share/applications/jedit.desktop[/SIZE]


and it worked instantly. I didn't even have to log out.

I don't know why the new rev of jEdit put it there.

Thanks you so much.


M....

---

