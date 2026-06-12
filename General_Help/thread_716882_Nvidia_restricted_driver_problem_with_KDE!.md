---
title: "Nvidia restricted driver problem with KDE!"
date: 2008-03-06
forum: General Help
---

### Post by hybrid- on 2008-03-06
Hi

Im running Kubuntu (KDE) and i have Nvidia GeForce Go 7600. I tried to install Nvidia 3D drivers trough "System Settings - Restricted Drivers", but install stops at some point and says: "There was an error committing changes. Possibly there was a problem downloading some packages or the commit would break packages". My internet connection should be ok, so maybe i have some program that blocks install?

Anyway, i started systemsettings trough console (root) and tried to install drivers again - same problem. I have tried to boot computer but that doesnt help. When I tried to install trough console, i got next lines to console (i dont understand much myself) : 

root@anttifly:~# systemsettings
Error: "/var/tmp/kdecache-eemeli" is owned by uid 1000 instead of uid 0.
adding Restricted Drivers /usr/share/applications/kde/restricted-manager-kde.des
ktop

Pythonize constructor -- pid = 7253
Python interpreter initialized!

Pythonize constructor -- pid = 7253
kapture::PkgSystem::PkgSystem()
kdecore (KProcess): WARNING: _attachPty() 32
adept_batch: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file adept_batc
hui.rc
kapture::PkgSystem::CreatePM()
kapture::DPkgPM::Go ()
DPkgPM::Go()
DPkgPM::runScripts ('DPkg::Pre-Invoke', 0)
DPkgPM::runScripts ('DPkg::Pre-Install-Pkgs', 1)
adept::DPkgPM::forkScript("/usr/sbin/dpkg-preconfigure --apt || true")
QObject::connect: No such signal konsolePart::processExited(const KProcess*)
QObject::connect:  (sender name:   'konsolepart')
QObject::connect:  (receiver name: 'unnamed')
kdecore (KProcess): WARNING: _attachPty() 33
a process exited!
END: adept::DPkgPM::forkScript("/usr/sbin/dpkg-preconfigure --apt || true")
DPkgPM::setupArgs ()
reading end of the pipe: 10
running '/usr/bin/dpkg --status-fd 32 --unpack /var/cache/apt/archives/nvidia-gl                                                                                                   x-new_100.14.19+2.6.22.4-14.10_i386.deb '
adept::DPkgPM::forkDpkg ()
QObject::connect: No such signal konsolePart::processExited(const KProcess*)
QObject::connect:  (sender name:   'konsolepart')
QObject::connect:  (receiver name: 'unnamed')
kdecore (KProcess): WARNING: _attachPty() 33
updateStatus( nvidia-glx-new, half-installed, )
updateStatus: msg =  Preparing installation of %1...
updateStatus: seen = 1, total = 5
a process exited!
a process exited!

Can anyone help? Can I force install drivers manually somehow? I tried to look something exceptional errors from /var/log/Xorg.0.log but i didn't find anything.

Many thanks
-Antti

---

