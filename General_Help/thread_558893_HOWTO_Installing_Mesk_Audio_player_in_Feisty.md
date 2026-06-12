---
title: "HOWTO: Installing Mesk Audio player in Feisty"
date: 2007-09-24
forum: General Help
---

### Post by howdyboby on 2007-09-24
This is a walk through on how to install the latest mesk audio player on Ubuntu Feisty.

[Mesk's website]("http://mesk.nicfit.net")

[LIST=1]
[*]run sudo apt-get install eyeD3 python-gtk2-dev librsvg2-dev libgstreamer0.10-dev python-pyvorbis libhal-dev python-cddb libdbus-glib-1-dev intltool python-pymad gstreamer0.10-plugins-ugly
[*]Download mesk source from [http://mesk.nicfit.net/releases/mesk-0.3.2.tgz]("http://mesk.nicfit.net/releases/mesk-0.3.2.tgz")

[/LIST]

Then run the following commands:

tar -zxf ./mesk-0.3.2.tgz
cd mesk-0.3.2
./configure --prefix=/usr
make
sudo make install

I have also made a [deb]("http://www.howdyboby.com/mesk/mesk-0.3.2-1.deb") package for it should you prefer to install it that way.

---

