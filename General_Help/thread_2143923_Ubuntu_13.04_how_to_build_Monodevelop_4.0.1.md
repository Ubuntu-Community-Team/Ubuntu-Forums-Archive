---
title: "Ubuntu 13.04: how to build Monodevelop 4.0.1?"
date: 2013-05-10
forum: General Help
---

### Post by Arsen.Shnurkov on 2013-05-10
[http://stackoverflow.com/questions/16485826/ubuntu-13-04-how-to-build-monodevelop-4-0-1](http://stackoverflow.com/questions/16485826/ubuntu-13-04-how-to-build-monodevelop-4-0-1)

I downloaded sources from git:
git clone git://github.com/mono/monodevelop.git
and dependencies:
cd monodevelop && git submodule init && git submodule update

I setup mono 3.0.11 (because "You need mono 2.10.9 or newer" and default version was 2.10.8.1)

I added repository: cat «deb [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) lucid main» >> /etc/apt/sources.list

I installed packages:
apt-get install libglib2.0-cil gnome-sharp2 gtk-sharp2 libmono-addins-cil-dev libmono-addins-gui-cil-dev libmono-addins-msbuild-cil-dev

./configure
gives me

Configuration Summary
---------------------

MonoDevelop has been configured with 
    prefix = /usr/local
    profile = default

Packages included in the build:
    main
    extras/JavaBinding
    extras/ValaBinding
    extras/MonoDevelop.Database
    extras/MonoDevelop.Debugger.Gdb
    extras/PyBinding
    extras/MonoDevelop.MeeGo

But
make | grep "not resolved"
gives me errors:
/usr/local/lib/mono/4.0/Microsoft.Common.targets: warning : Reference 'glib-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' not resolved
/usr/local/lib/mono/4.0/Microsoft.Common.targets: warning : Reference 'pango-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' not resolved
/usr/local/lib/mono/4.0/Microsoft.Common.targets: warning : Reference 'atk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' not resolved
/usr/local/lib/mono/4.0/Microsoft.Common.targets: warning : Reference 'gdk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' not resolved
/usr/local/lib/mono/4.0/Microsoft.Common.targets: warning : Reference 'gtk-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' not resolved
/usr/local/lib/mono/4.0/Microsoft.Common.targets: warning : Reference 'glade-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' not resolved

In this page - [http://article.gmane.org/gmane.comp.gnome.mono.monodevelop.general/14338](http://article.gmane.org/gmane.comp.gnome.mono.monodevelop.general/14338) it is recommended «It looks like you need to install gtk-sharp 2.12.x»

But I have them installed:

find /usr/lib/mono/gac -xdev -iname "*Sharp.dll" | grep "3c99f" | grep -v "policy"
/usr/lib/mono/gac/pango-sharp/2.12.0.0_35e10195dab3c99f/pango-sharp.dll
/usr/lib/mono/gac/gconf-sharp/2.24.0.0_35e10195dab3c99f/gconf-sharp.dll
/usr/lib/mono/gac/gnome-sharp/2.24.0.0_35e10195dab3c99f/gnome-sharp.dll
/usr/lib/mono/gac/gtk-sharp/2.12.0.0_35e10195dab3c99f/gtk-sharp.dll
/usr/lib/mono/gac/atk-sharp/2.12.0.0_35e10195dab3c99f/atk-sharp.dll
/usr/lib/mono/gac/glib-sharp/2.12.0.0_35e10195dab3c99f/glib-sharp.dll
/usr/lib/mono/gac/art-sharp/2.24.0.0_35e10195dab3c99f/art-sharp.dll
/usr/lib/mono/gac/gnome-vfs-sharp/2.24.0.0_35e10195dab3c99f/gnome-vfs-sharp.dll
/usr/lib/mono/gac/glade-sharp/2.12.0.0_35e10195dab3c99f/glade-sharp.dll
/usr/lib/mono/gac/gdk-sharp/2.12.0.0_35e10195dab3c99f/gdk-sharp.dll

I also tried this advice:
[http://www.mono-project.com/Parallel_Mono_Environments#Tip:_MONO_GAC_PREFIX](http://www.mono-project.com/Parallel_Mono_Environments#Tip:_MONO_GAC_PREFIX)
and add MONO_GAC_PREFIX into ~/.bashrc
echo $MONO_GAC_PREFIX
/usr

But compiling errors are still here. What I should do?

---

