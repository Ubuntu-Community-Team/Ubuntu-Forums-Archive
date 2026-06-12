---
title: "How to install OBApps (.tar.gz) in Lubuntu 13.04?"
date: 2013-07-12
forum: General Help
---

### Post by vasa1 on 2013-07-12
OBApps is a graphical tool for making per-app window settings in Lubuntu. Unfortunately, it is currently not available in the Software Center or by means of a ppa.

It is available [here]("https://sourceforge.net/projects/obapps/files/obapps-0.1.7.tar.gz/download") but in .tar.gz format.

I downloaded that file and extracted it to my desktop: ~/Desktop/obapps-0.1.7. There's a README provided and it mentions that  **wxPython (2.8.0+)** and **python-xlib** are requirements (=dependencies?).

The second one, python-xlib, is in the repos but it took me a while to figure out what wxPython was all about. Anyway, after reading around, I got to [http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian) which seemed to indicate that installing 
python-xlib
python-wxgtk2.8
python-wxtools
wx2.8-il8n

would be sufficient. Fortunately, all of these are in the repo.

After installing these "requirements", I ran **sudo python setup.py install** from a terminal opened to ~/Desktop/obapps-0.1.7. The installation was successful and I now have a GUI way to make settings for specifying how a particular app opens:
[LIST=1]
[*]whether its decorated or not
[*]whether it opens minimized or maximized or any size in between
[*]its exact position on my screen
[*]which desktop it opens on
[*]whether it should have focus or not
[/LIST] 

It's possible to do all this without installing OBApps just by editing the [applications section in lubuntu-rc.xml]("https://help.ubuntu.com/community/Lubuntu/Windows#Launching_Windows_Maximized") but I wanted to get the GUI thing going.

Once OBApps is successfully installed, the obapps-0.1.7 folder used for installation can be removed but it's worth retaining the README.

---

