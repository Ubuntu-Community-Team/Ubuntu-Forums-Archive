---
title: "How to create a launcher for a NFC tag writting app?"
date: 2020-09-16
forum: General Help
---

### Post by suomalainen on 2020-09-16
Hello Everybody!

I want to write some NFC tags and learned of a program called TagXplorer that I can use to do this. I now have everything working but want to create a launcher to make things easier. Here is what I have done.

I have a file called 'TagXplorer-v1.2.jar" that I downloaded from here:

[https://www.nxp.com/products/rfid-nfc/mifare-hf/mifare-desfire/tagxplorer-pc-based-nfc-tag-reader-writer-tool:TAGXPLORER](https://www.nxp.com/products/rfid-nfc/mifare-hf/mifare-desfire/tagxplorer-pc-based-nfc-tag-reader-writer-tool:TAGXPLORER)


I then went to:

[https://community.nxp.com/t5/NFC/TagXplorer-v1-2-jar-cannot-start/m-p/918596](https://community.nxp.com/t5/NFC/TagXplorer-v1-2-jar-cannot-start/m-p/918596)

and learned that if I want to launch the file 'TagXplorer-v1.2.jar" I must then go to:

[https://gluonhq.com/products/javafx/](https://gluonhq.com/products/javafx/)

and download and extract the file "JavaFX Linux SDK"

So I did this all this.

On my desktop there is now a folder called 'javafx-sdk-11.0.2' and in this folder is the 'lib' folder. In addition to this the 'TagXplorer-v1.2.jar" file also resides on my desktop.


If I want to run TagXplorer I open terminal and issue the following:


cd Desktop

java --module-path /home/suomalainen/Desktop/javafx-sdk-11.0.2/lib/ --add-modules javafx.controls,javafx.fxml -jar TagXplorer-v1.2.jar


TagXplorer opens and I'm a happy camper!


The thing is I'd rather have a folder tucked away in my home directory for these files and a launcher in my top panel which I can double click to open TagXplorer.

Is this or some other better way possible so that I don't need to keep these folders on my Desktop?

What can I do?

Thank you!

Suomalainen

---

### Post by CatKiller on 2020-09-16
The launchers used for menu entries, panel widgets, and context menus are specified by .desktop files, which are just text files with a standardised syntax.

There is a specification for them, but you'll probably get the gist by just dragging and dropping some menu entries into a text editor.

There are standard locations to put them if you want them to appear in menus, and Gnome's default file browser (and possibly KDE's, too, I'm not sure) have restricted one's ability to launch them from other arbitrary locations. Gnome also removed the ability to launch them from the Desktop, although I understand that functionality can be restored through an extension.

---

