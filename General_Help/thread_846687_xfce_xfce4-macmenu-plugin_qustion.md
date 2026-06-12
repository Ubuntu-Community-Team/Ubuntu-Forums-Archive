---
title: "xfce xfce4-macmenu-plugin qustion"
date: 2008-07-01
forum: General Help
---

### Post by natman3400 on 2008-07-01
Sorry if I have brung up a old issue but how do i install xfce4-macmenu-plugin.
Please explain in a easy to understand manor.

---

### Post by whollycow on 2008-07-15
Well, that depends on your system configuration.  If you are running GNOME, you can find preconfigured install packages (debs) at the google code page [[COLOR="Red"]here[/COLOR]]("http://code.google.com/p/gnome2-globalmenu/downloads/list").

Assuming that you are running Hardy, download the file for Hardy (gnome-globalmenu-0.4-svn964.tar.gz).

For these purposes, I'll assume the file is sitting on your desktop, if it's not, you'll need to change the directories accordingly.

Open a terminal and cd to the Desktop:
cd Desktop

Untar the file: 
tar -xvzf gnome-globalmenu-0.4-svn964.tar.gz

CD into the new directory:
cd globalmenu

Unpack the debs:
sudo dpkg -i *.deb

Viola, you should be able to add the global menu applet to your GNOME panel.

edit: Oops, I just realized you were asking about the xfce packages.  I think you're out of luck if you're looking for an easy way to do those.  I haven't seen anything.

---

### Post by armag.info on 2009-11-27
[whollycow]("http://ubuntuforums.org/member.php?u=350306")
 don't be blind. natman was asking a) about XFCE, not GNOME b) macmenu-plugin (not globalmenu-plugin). Feel the difference.

I'm also interested, has anybody tried to install xfce-macmenu-plugin onto Xubuntu? Any heroes? Please, share the experience on installation.

---

### Post by mttza1 on 2010-02-15
If you've got a source tarble then extract it and cd into the directory (in a terminal)

then either run ```
sudo ./configure
``````
sudo make
```and```
sudo make install
```

or without configure, read the INSTALL, or README file (if theres no INSTALL file).

If you hava a debian package (.deb), then just open it in gdebi (the installer).

you can then right click on the panel you want to add it to, click Add and find the plugin.

I'd be interested to see if it installs properly, as i'm trying to get the Xfce plugin of gnome2-globalmenu working (a new version, based on macmenu).

mttza1

---

