---
title: "QGL Viewer Install"
date: 2008-03-09
forum: General Help
---

### Post by islam_ce on 2008-03-09
Hi All,
I want to install QGLViewer from Adept Manager.But the package is not available.According to following link([COLOR="Blue"]Do not install qglviewer with your package manager (adept, synaptics) because there are two different packages (written by different authors) that have the same name. Consequently libqglviewer upon adding to debian will be renamed to a different name: lib3dviewer.)[/COLOR] I tried to install
[http://yade.wikia.com/wiki/New:Porting_QGLViewer_to_kubuntu](http://yade.wikia.com/wiki/New:Porting_QGLViewer_to_kubuntu)

They said...
you have to add following line: 
deb-src [http://blabluga.hell.pl/QGLViewer/sid](http://blabluga.hell.pl/QGLViewer/sid)

and [COLOR="Red"]Click "Add", "Apply", "Close", then click "Fetch Updates" so that adept will know that there is a source of a new package qglviewer available.[/COLOR]

But after  doing this I lost Adept Manager.Any idea how can I back Adept Manager like, K>System>Adept Manager. or any idea how can I add the qgl viewer in Adept Manager or How can I install QGL Viewer package...

[COLOR="Navy"](New to Kubuntu)[/COLOR]

Regards.
Nurul Islam

---

### Post by eudoxos on 2008-05-16
Hi, qglviewer packages in ubuntu (hardy) are broken. Instead we integrated qglviewer code into our sources and if you use the SVn version (which is recommended anyway), you don't have to "port" qglviewer. See [http://yade.wikia.com/wiki/Installation_of_yade_on_debian_or_kubuntu](http://yade.wikia.com/wiki/Installation_of_yade_on_debian_or_kubuntu) for details. Sorry for late answer.

---

