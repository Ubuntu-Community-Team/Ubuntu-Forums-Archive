---
title: "Restore Ubuntu to original state"
date: 2007-11-01
forum: General Help
---

### Post by hayesbcaj on 2007-11-01
I recently installed kubuntu on top of ubuntu then removed kubuntu. As a result things are starting to get a little strange. My splash screens are gone (boot, shutdown...) the little starting services box on gnome startup is gone. I've tried all the howto's on changing the splash screens with no success. I now get some error messages here and there. Overall my system is a little slower than it was before kubuntu. It's now as slow as kubuntu was when i had it up and running...the reason i got rid of it. Anyway, I would prefer not to mess around with a bunch of fixes, is there any way to get ubuntu back to its original state without losing my personal data? And without having to back up all my data? I don't mind if desktop settings are lost or even if some apps are lost, i can reinstall and change settings again.
Thanks, Bill

---

### Post by strabes on 2007-11-01
I assume that you used apt-get to install and remove kubuntu? apt-get is terrible at dependency handling and won't remove most of the library packages installed by kubuntu-desktop. The only solution I can think of that might work is this:```
sudo apt-get purge kubuntu-desktop && sudo aptitude update && sudo aptitude install kubuntu-desktop && sudo aptitude purge kubuntu-desktop
```

You might want to open a root terminal for this command so you can leave it alone since it will probably take awhile if it has to download everything again. To do this, run "sudo -s"

---

### Post by hayesbcaj on 2007-11-02
I installed and removed kubuntu using synaptic only to find out that didn't do the trick. So I searched the web and found the following command:

```

sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts debtags digikam dolphin enscript fftw3 foomatic-db-gutenprint gdebi-kde gnupg-agent gpgsm gtk-qt-engine gwenview hplip-gui hwdb-client-kde ijsgutenprint k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdesudo kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate kio-umountwrapper kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvkbd kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libclucene0 libcluceneindex0 libdbus-qt-1-1c2 libept0 libexiv2-0 libflac++6 libgmp3c2 libgpgme11 libid3tag0 libifp4 libijs-0.35 libimlib2 libjpeg-progs libk3b2 libkbluetooth0 libkcal2b libkcddb1 libkdcraw1 libkdepim1a libkexiv2-1 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libksba8 libkscan1 libksieve0 libktnef1 liblua50 liblualib50 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libopenexr2c2a libopenobex1 libpoppler-qt2 libpq5 libpth20 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui librsync1 libruby1.8 libsamplerate0 libsearchclient0 libskim0 libsmokeqt1 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtunepimp5 libungif4g libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxcb1 libxine1 libxvmc1 mysql-common network-manager-kde networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pinentry-qt poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-qt4-dbus python-sip4 python2.5-dev qca-tls rdiff-backup restricted-manager-kde ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch strigi-applet strigi-daemon && sudo apt-get install ubuntu-desktop

```

This did the trick in removing everything kubuntu (I think). But i can't get my pc back to its original state. Everything seems to work ok but performance took a slight hit and I can't get the splash screens back. I tried following the tutorials on changing the splash screens but didn't work. The symbolic links are still there and pointing to the correct files. Pre kubuntu, ubuntu performed beautifully. Now, not as good. I suppose I'll start backing up to get ready for a fresh install just in case.

---

### Post by nick_h on 2007-11-02
For the splash screen try:
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure usplash
```

---

### Post by hayesbcaj on 2007-11-03
I finally got the startup and shutdown splash screens to reappear. In the process I tried setting a grub splash screen. No success with that, each time i boot i get an error:
Failed to read splash image........
Press any key to continue.

While trying to sort out the problem I've left the grub boot image line in and just kept kitting any key to get to the grub menu and boot as normal. Now, All of a sudden, pressing any key no longer moves the process along. I'm stuck with this error message and can't proceed any further in the boot process. 
One last note, the last shutdown before this error was by holding the power button as the last boot process got stuck and became unresponsive.
What can I do? I can't afford to lose all my data.

---

### Post by nick_h on 2007-11-03
If you can't get it to boot then use the Live CD.  Then correct the problem in your /boot/grub/menu.lst and try again.  You could always run fsck from the Live CD if you need to.

---

### Post by hayesbcaj on 2007-11-05
Turns out my usb keyboard was not working at boot time. I had to use one of those usb to ps2 adapters and it worked so i was able to hit any key to continue. Now I notice that after leaving the grub menu but before the startup splash screen with progress bar pops up, I get a flash of the ubuntu brown color at the bottom quarter of the screen. After the flash it will go to the regular splash screen with progress bar (a couple of times I've had the flash pop up but all garbled not brown and my pc will hang and have to do hard reboot). Seems like something is trying to load somewhere but having a resolution problem. I'm not sure where to look at this point.

---

### Post by nick_h on 2007-11-05
I get a similar effect - a short burst of colour at the top of my screen.  I never got this with Dapper but do with Feisty and Gutsy.  Setting the vga= boot option in grub changes it to a short burst of terminal text.

---

