---
title: "Making a deb of a python script"
date: 2006-11-26
forum: General Help
---

### Post by ihavenoname on 2006-11-26
Ok, here's the deal. A friend and I are making a python program (with a gui made using glade) We are almost done (well, with our first version). We would like to package the program and have an icon place either on the panel or in the Applications menu or on the desktop. We plane to use reconstructor to make a custom Ubuntu cd to showcase our program and OSS. We don't really know how to make deb packages. All the how-tos are for programs that require compilation using make (at least the ones we have found). Can anyone point us to where we can find out how to accomplish these tasks? Or help us in anyway?  The program is part of a school project (for some kind of community service. ) It's an educational program. (math). It is due around dec. 8th. If you need any more information feel free to ask. And if anyone wants to test it, it would be great. Thanx!

---

### Post by 23meg on 2006-11-26
[This]("http://easy-deb.sourceforge.net/") may help.

---

### Post by RAOF on 2006-11-26
I've done the packaging for Specto, and that's a pure-python program.  If you've made a *setup.py* using python's distutils, packaging it should be trivial.

You may want to grab the source packages for Specto from my repository (or any other pure-python program from the official repositories)- they may be a good reference for you.

---

