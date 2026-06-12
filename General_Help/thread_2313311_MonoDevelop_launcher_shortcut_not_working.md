---
title: "MonoDevelop launcher shortcut not working"
date: 2016-02-11
forum: General Help
---

### Post by soxterix on 2016-02-11
I installed MonoDevelop using following commands:

> sudo add-apt-repository ppa:ermshiperete/monodevelop
sudo apt-get update
sudo apt-get install monodevelop-current


And I can launch application via terminal using: 

> /opt/monodevelop/bin/monodevelop-launcher.sh

but I can't launch it by typing "monodevelop" in terminal and there is no icon in launcher. I copied monodevelop.desktop file (which was located in /opt/monodevelop/share/applications) to /usr/share/applications/ and it's not working. What can I do about it?

monodevelop.desktop looks like this:
> [Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=MonoDevelop
GenericName=Integrated Development Environment
GenericName[ja]=&#32113;&#21512;&#38283;&#30330;&#29872;&#22659;
Comment=Develop .NET applications in an Integrated Development Environment
Comment[ja]=.NET&#12450;&#12503;&#12522;&#12465;&#12540;&#12471;&#12519;&#12531;&#38283;&#30330;&#12434;&#34892;&#12358;&#12383;&#12417;&#12398;&#32113;&#21512;&#38283;&#30330;&#29872;&#22659;
Exec=monodevelop %F
TryExec=monodevelop
Icon=monodevelop
StartupNotify=true
Terminal=false
Type=Application
MimeType=text/x-csharp;application/x-mds;application/x-mdp;application/x-cmbx;application/x-prjx;application/x-csproj;application/x-vbproj;application/x-sln;application/x-aspx;text/xml;application/xhtml+xml;text/html;text/plain;
Categories=GNOME;GTK;Development;IDE;
X-GNOME-Bugzilla-Bugzilla=Ximian
X-GNOME-Bugzilla-Product=MonoDevelop
X-GNOME-Bugzilla-OtherBinaries=monodevelop

---

