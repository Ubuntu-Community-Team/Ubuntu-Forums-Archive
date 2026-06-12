---
title: "libqt3-mt without OpenGL on edgy?"
date: 2007-04-05
forum: General Help
---

### Post by RSkog on 2007-04-05
Hello

I am trying to compile an application using qt3 with opengl. I get alot of "undefined reference to 'QGLWidget::...'" when linking.

It seems as though libqt3-mt.so does not come with OpenGL support. If I do 'objdump -T /usr/share/qt3/lib/libqt-mt.so | grep -i qglwidget' I get nothing. Doing the same on a Dapper installation prints out lots and lots of symbols.

My libqt3-mt package version is 3:3.3.6-3ubuntu3

I assume people are running qt3 applications with opengl on their Edgy installations so I cant figure out why I cannot find the opengl stuff in my libqt3-mt. Can the package install different files depending on hardware support for opengl or something?

Any help is appreciated.

Regards,
Richard Skog

---

### Post by tbroderick on 2007-04-05
You got libqt3-mt-dev installed?

---

### Post by RSkog on 2007-04-06
Yes I do have libqt3-mt-dev installled. Package version is 3:3.3.6-3ubuntu3..

If I do:

$ dpkg --search /usr/lib/libqt-mt.so.3.3.6
libqt3-mt: /usr/lib/libqt-mt.so.3.3.6

Which would indicate the lib is indeed from the libqt3-mt package. This is also the case on a dapper installation.

It would be interesting to know if any of you with edgy installations have any qglwidget symbols in your libqt-mt-so. Please try: 'objdump -T /usr/share/qt3/lib/libqt-mt.so | grep -i qglwidget' and see if you get anything.

/Richard

---

### Post by tbroderick on 2007-04-06
I don't have qt installed anymore, but do you have the gl-dev packages, libgl1-mesa-dev, libglu1-mesa-dev and freeglut3-dev installed?

---

### Post by RSkog on 2007-09-29
As it turns out even though the libqt3-mt package was installed the actual so file was replaced by an installation of drivers for a Samsung SCX-4521F printer (see [http://www.hathawaymix.org/Weblog/2005-07-15](http://www.hathawaymix.org/Weblog/2005-07-15) for people with similar problems with the Samsung install). 

Anyways, I reinstalled the libqt3-ml package and everything was fine (don't know if that broke the printer drivers since I don't have that printer anymore).

/Richard

---

