---
title: "Unable to add the fluxbuntu cd as a repository"
date: 2007-10-30
forum: General Help
---

### Post by TeeAhr1 on 2007-10-30
Howdy, y'all.  I'm trying to add the Fluxbuntu 7.10rc CD as a repository so I can run it parallel to my existing Kubuntu install, but I get this error: "Error scanning the CD E:Sub-process gpgv returned an error code (2), W:Signature verification failed for: /cdrom/dists/gutsy/Release.gpg"

What gives?

best-
pete

---

### Post by ruibernardo on 2007-10-31
Hi,

did you try with apt-cdrom? It should work.

---

### Post by gottferdamnt on 2007-10-31
Same issue here...

---

### Post by TeeAhr1 on 2007-10-31
> **epimeteo said:**
> Hi,

did you try with apt-cdrom? It should work.

Same error.

---

### Post by TeeAhr1 on 2007-11-03
*bump*

---

### Post by ruibernardo on 2007-11-03
Did you run it with sudo? What was the output of apt-cdrom?
```
sudo apt-cdrom add
```

---

### Post by TeeAhr1 on 2007-11-03
```
teeahr1@no2pencil:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [e71b3b97b109dcdf30f2fdcc5e535e9b-2]
Scanning disc for index files..
Found 1 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Fluxbuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071026)'
This disc is called:
'Fluxbuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071026)'
Copying package lists...gpgv: Signature made Fri 26 Oct 2007 12:49:51 PM CDT using DSA key ID B6A4EB33
gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/gutsy/Release.gpg
```

---

### Post by ruibernardo on 2007-11-03
Only Alternate CDs and DVDs can be added as a repository. 

When you booted that CD was it a LiveCD? Did you have a graphic environment? If you did, it's a LiveCD and you can't use it as a repository. For example, you can't use the Ubuntu Desktop CD as a repository, only the Alternate CD and DVD (text mode installation and no GUI when booted - only install) can be used as a repository.

---

### Post by TeeAhr1 on 2007-11-04
It is an alternate CD (there isn't a live CD for the Fluxbuntu rc, there will be one for the final release).  Anyway, here's what I did (the sloppy solution) after which I will describe the better solution.

What Pete Did
1. Copy the "dists" and "pool" folders off the CD.  Put them anywhere you like.
2. Delete the "Release.gpg" file from /dists/gutsy
3. Burn the two folders onto a new CD
4. Run "sudo apt-cdrom add".  It'll prompt you to name the CD and put it in your sources.list

Okay, now for the more elegant solution, which I didn't figure out until I had already done it the kludgy way. (I HAVE NOT DONE THIS, TRY AT YOUR OWN RISK)
1. Put in the Fluxbuntu CD and go to /media/cdrom/pool/main/u/ubuntu-keyring
2. Install the ubuntu-keyring deb from there, by itself.
3. sudo apt-cdrom add
4. After installing the packages you want to install, it's probably going to be desirable to remove the cd from sources.list and reinstall the repository version of ubuntu-keyring.

Okay, problem one solved.  We've got packages.  Here's what I get when I run "sudo apt-get install fluxbuntu-desktop":
```
  abiword abiword-common abiword-plugins alsamixergui arj bluez-utils claws-mail dia dia-common dia-libs displayconfig-gtk doc-base docbook-xml fbpager
  fluxbox fluxbuntu-artwork fluxbuntu-default-settings fluxbuntu-desktop fluxconf gdk-imlib11 gksu gnumeric-common gnumeric-gtk gstreamer0.10-esd
  gstreamer0.10-plugins-base-apps gstreamer0.10-tools gtk2-engines gtk2-engines-pixbuf gtk2-engines-salsa gvidm imagemagick imlib-base irssi ivman
  kazehakase language-selector leafpad lesstif2 liba52-0.7.4 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libatk1-ruby1.8
  libavformat1d libbeecrypt6 libcairo-ruby1.8 libcompfaceg1 libdc1394-13 libdvbpsi4 libdvdnav4 libebml0 libenchant1c2a libetpan11 libfltk1.1
  libgdk-pixbuf2-ruby1.8 libgdome2-0 libgdome2-cpp-smart0c2a libgettext-ruby1.8 libglib1.2 libglib2-ruby1.8 libgnome2-canvas-perl libgnome2-perl
  libgnome2-vfs-perl libgoffice-0-4 libgoffice-0-common libgsf-gnome-1-114 libgtk1.2 libgtk1.2-common libgtk2-ruby libgtk2-ruby1.8 libgtkmathview0c2a
  libhesiod0 liblaunchpad-integration0 liblink-grammar4 liblircclient0 liblockfile1 libmatroska0 libmozjs0d libmpeg2-4 libneon25 libnm-glib0 libnotify1
  libots0 libpango1-ruby1.8 libpurple0 librpm4 librsvg2-common libscrollkeeper0 libt1-5 libtar libvcdinfo0 libvlc0 libvte-common libvte9 libwmf0.2-7
  libwpd-stream8c2a libwxbase2.6-0 libwxgtk2.6-0 libxosd2 libxul-common libxul0d libzephyr3 link-grammar-dictionaries-en menu network-config p7zip-full
  pidgin pidgin-data pkg-config pmount python-notify restricted-manager rox-filer rpm salsa-icon-theme scim scim-gtk2-immodule scim-modules-socket
  scim-modules-table scim-tables-additional screensaver-default-images scrollkeeper sgml-data slim synaptic usplash-theme-fluxbuntu vlc vlc-nox w3m-img
  xarchiver xbitmaps xlockmore xmms xpdf xpdf-common xpdf-reader xscreensaver-gl xterm xzgv zenity
```

Needless to say, I'm a little bit nervous about letting that fly..  Lots of stuff there, and I don't know if there would be conflicts.  If anyone else out there in TV Land has a spare rig that they want to test this out on, let me know if it works for you.  Until then, I'll keep stabbing at this.

Best-
Pete

---

### Post by tsmets on 2007-11-06
same issue here ...
repository are the one from  belgium and austria ...
3 cd lost :)

Any idea ...?

\T,

---

