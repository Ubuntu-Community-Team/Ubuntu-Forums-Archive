---
title: "Ubuntu Wine MS Word"
date: 2013-01-12
forum: General Help
---

### Post by YungKris15 on 2013-01-12
Hey guys, I'm new to Ubuntu, and I love it so far.

I've installed Wine successfully, along with MS Word. But for the life of me, I can't figure out how the hell to open Word.

I searched it on the Dash Home, and it isn't showing the application.

Would you guys happen to know what it is that I'm doing wrong? Here's the screenshot of what I have:

[IMG]http://www.krissales.me/shots/shot1-12-2013-2:20PM.png[/IMG]

Not sure what I'm suppose to do.

---

### Post by Mark Phelps on 2013-01-12
If you need to use Word daily, and need to rely on all of its features working -- then trying to do this using Ubuntu is going to be an exercise in frustration, especially, if you are going to be receiving Word docs using the ".docx" file extension.

See the WineHQ page below about Word.  The Silver rating means one or more major features don't work: 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=10]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=10")

---

### Post by TheFu on 2013-01-12
I haven't used Unity in over a year, but in the old-style menu system, there would be a WINE --> Ms-Word menu item.  There might be a **word.desktop** or **winword.desktop** file somewhere that you can run by double clicking too.  

Sorry that I'm not more help.

For my needs, I required 100% compatibility when I couldn't use libreoffice. That meant running MS-Office inside a virtual machine under something like KVM or VirtualBox.

---

### Post by Pilot6 on 2013-01-12
I suggest to install MS Office using PlayOnLinux. It is easy and works flawlessly.

---

### Post by samwillc on 2013-01-12
Hi YungKris15.

This may be your lucky day as I only did this a few hours ago myself!

[http://www.makeuseof.com/tag/easily-install-microsoft-office-2007-linux/](http://www.makeuseof.com/tag/easily-install-microsoft-office-2007-linux/)

This is what you're after. It's really easy.

Then, go to dash > playonlinux > select word/excel/whatever > press run.

A few things to note:

a) Opening it in this way could be a little annoying for someone who uses it a lot.
b) Remember when saving a file, it will by default save to a virtual C drive. Make sure you select your proper ubuntu 'documents' folder as destination.
c) I have not tested all sorts of things so could not tell what works/doesnt. Saving a document does work however!
d) Double clicking on a docx file in my documents opened the file in libreoffice, I could not find a way for it to automatically open in the relevant office program, although it may be possible.
e) I have not found a way to put a launcher shortcut to the individual programs i.e. I use cairo doc, I wanted word/excel/powerpoint all to have their own little icons. You can't pin playonlinux to cairo either as that then pins a python symbol to the dock (?! lol) Launch using method I described, then if you figure out the launcher stuff, please report back!

I will probably install windows in a virtual machine rather than doing all this when I get a new laptop and install office on that.

Right now I am running ubuntu 12.04 on an ancient gateway laptop with a missing 'h' key. The missing key makes typing this really awkward.

I hope this helps!

Sam.

---

