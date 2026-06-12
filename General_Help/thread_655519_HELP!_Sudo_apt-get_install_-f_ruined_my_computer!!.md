---
title: "HELP! Sudo apt-get install -f ruined my computer!!!"
date: 2008-01-01
forum: General Help
---

### Post by Dojan5 on 2008-01-01
AGH!!!!!
When installing a .deb packagefile, it asked me to run Sudo apt-get install -f and, i didnt think before i acted, now i cant run terminal firefox nothing!!!!
Okay, i installed KDE earlier (Thank GOD!) and it didnt affect the KDE apps...
Luckily i closed the terminal before the process was finished...
PLEASE HELP!
I messed this up and, what the heck should i do.
Im afraid that if i reboot, i wont be able to turn on the computer...
Thanks, i hope
/
Upset Joel

---

### Post by ~LoKe on 2008-01-01
You closed the terminal before the process was finished...why on earth did you do that?  apt-get -f install won't break anything; run it again.

---

### Post by Dojan5 on 2008-01-01
sudo apt-get install -f uninstalled EVERYTHING!
All of a sudden the networking thing dont work!
I got scared and closed the terminal...
AND NOW I CANT RUN THE TERMINAL AGAIN!
Thats the problem... Plus i cant run FireFox umm, Synaptic Add/Remove Programs (Same as synaptic i know)
PLUS a hell lot of files is missing to run other programs...

---

### Post by ~LoKe on 2008-01-01
I'm not sure you understood the output...and stopping the process midway isn't exactly safe.

Press Ctrl+Alt+F1 and you'll find yourself on a black screen with a command line.  Log in (you won't see the password being typed) then type:
```
sudo apt-get update && sudo apt-get upgrade
```
Tell me what happens.

---

### Post by Dojan5 on 2008-01-01
NOTHING!
ctrl + alt + f1 bring a black screen up...
And there is this thing indicating, well, something... only like a white _ just thicker that is blinking...
When i type, nothing comes up...

---

### Post by anjilslaire on 2008-01-01
The command
"sudo apt-get install -f"

FIXES broken install packages. It doesnt break everything or remove everything.

---

### Post by anjilslaire on 2008-01-01
> **Dojan5 said:**
> NOTHING!
ctrl + alt + f1 bring a black screen up...
And there is this thing indicating, well, something... only like a white _ just thicker that is blinking...
When i type, nothing comes up...

Reboot again & choose recovery mode

---

### Post by ~LoKe on 2008-01-01
> **Dojan5 said:**
> NOTHING!
ctrl + alt + f1 bring a black screen up...
And there is this thing indicating, well, something... only like a white _ just thicker that is blinking...
When i type, nothing comes up...

Try ctrl+alt+f2 or f3.

---

### Post by Dojan5 on 2008-01-01
Let me guess, it is removing and then fixing the broken packages....
Then, i interupted it when it was removing and....
Is it possible to run a repair install on Ubuntu (I have the live cd) without any file losses or will this problem be fixable in ubuntu without a terminal??? And no synaptic.... Possible to correct it with the Konsole in KDE?

---

### Post by Dojan5 on 2008-01-01
> **~LoKe said:**
> Try ctrl+alt+f2 or f3.
Nope.... Nothing...
I do have the KDE Konsole tho...
Possible to do it through the Konsole or?

---

### Post by ~LoKe on 2008-01-01
> **Dojan5 said:**
> Let me guess, it is removing and then fixing the broken packages....
Then, i interupted it when it was removing and....
Is it possible to run a repair install on Ubuntu (I have the live cd) without any file losses or will this problem be fixable in ubuntu without a terminal??? And no synaptic.... Possible to correct it with the Konsole in KDE?
If you can log into KDE and open up a terminal of any kind, great!  Do it, then run:

```
sudo apt-get update && sudo apt-get upgrade
```
It if complains about not working, then try:
```
sudo apt-get -f install
```

---

### Post by anjilslaire on 2008-01-01
If KDE is functional, you can try that as well. You may want to try the Recover mode option from GRUB to get a functioning terminal prompt, too.

---

### Post by Dojan5 on 2008-01-01
> **~LoKe said:**
> Try ctrl+alt+f2 or f3.
> **anjilslaire said:**
> Reboot again & choose recovery mode
Do i dare???
What if theres some important file missing and it wont start up again...
And, how do i choose recovery mode?

---

### Post by jamaisvu on 2008-01-01
> **Dojan5 said:**
> AGH!!!!!
When installing a .deb packagefile, it asked me to run Sudo apt-get install -f

[FONT=Franklin Gothic Medium]To quote the How To ([https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)), this is 'the same as “Edit->Fix Broken Packages” and “Apply” in synaptic. Do this if you get complaints about packages with “unmet dependences”'.
[/FONT]
> and, i didnt think before i acted, now i cant run terminal firefox nothing!!!!
Okay, i installed KDE earlier (Thank GOD!) and it didnt affect the KDE apps...
Luckily i closed the terminal before the process was finished...

[FONT=Franklin Gothic Medium]That's actually the most likely thing to have left you with broken packages.
[/FONT]
> PLEASE HELP!
I messed this up and, what the heck should i do.
Im afraid that if i reboot, i wont be able to turn on the computer...
Thanks, i hope
/
Upset Joel

[FONT=Franklin Gothic Medium]I would probably try, presuming that your KDE works and your GNOME is horribly broken:
[/FONT]
[FONT=Courier New]sudo apt-get autoremove ubuntu-desktop [FONT=Franklin Gothic Medium](this sounds scarier than it is!)[/FONT]
sudo apt-get install ubuntu-desktop
sudo apt-get upgrade
[/FONT]
[FONT=Franklin Gothic Medium]This should give you a clean install of GNOME and Firefox. Alternatively, it will bring up some interesting errors -- you can of course select (probably easiest with the mouse) and copy text from Konsole and paste it here.
[/FONT]

---

### Post by ~LoKe on 2008-01-01
> **Dojan5 said:**
> Do i dare???
What if theres some important file missing and it wont start up again...
And, how do i choose recovery mode?

Don't bother with that.  You said you can get into KDE, so do that, then run the commands I posted.

---

### Post by Dojan5 on 2008-01-01
> **~LoKe said:**
> Don't bother with that.  You said you can get into KDE, so do that, then run the commands I posted.

Okay, um, well, i couldnt log in again... Of some reason... Then i ran the recovery mode thingy and ran sudo apt-get install -f again...
It uninstalled the rest of the things and i said "rebbot" it rebooted...
Then i was able to log in, but it said something about that the GNOME session wasnt valid again and that i have to choose a new session...
And when i did that, GNOME aint listed anymore...
I dont think i have GNOME... :S
Well, running the commands

---

### Post by ~LoKe on 2008-01-01
> **Dojan5 said:**
> Okay, um, well, i couldnt log in again... Of some reason... Then i ran the recovery mode thingy and ran sudo apt-get install -f again...
It uninstalled the rest of the things and i said "rebbot" it rebooted...
Then i was able to log in, but it said something about that the GNOME session wasnt valid again and that i have to choose a new session...
And when i did that, GNOME aint listed anymore...
I dont think i have GNOME... :S
Well, running the commands

Try...
```
sudo apt-get install ubuntu-desktop gnome-desktop-environment
```

---

### Post by Dojan5 on 2008-01-01
Yer so fast... Well this is what those thingy you asked me before say:
> 
[sudo] password for joel:
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-sv_SE
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-sv_SE
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-sv_SE
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-sv_SE
Läs:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Läs:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release.gpg [189B]
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Translation-sv_SE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-sv_SE
Läs:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-sv_SE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-sv_SE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-sv_SE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-sv_SE
Läs:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-sv_SE
Bra [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Bra [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Bra [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release
Läs:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [187B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-sv_SE
Läs:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-sv_SE
Läs:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-sv_SE
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-sv_SE
Bra [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Läs:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release [58,5kB]
Bra [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Bra [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Bra [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages
Bra [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Bra [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Bra [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Sources
Bra [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Bra [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Bra [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Bra [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Bra [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Läs:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages [24,8kB]
Läs:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages [86,0kB]
Läs:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages [7570B]
Läs:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages [4263B]
Läs:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Sources [4711B]
Läs:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources [25,7kB]
Läs:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources [1190B]
Läs:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources [937B]
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources
Bra [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
Hämtade 215kB på 8s (25,1kB/s)
Läser paketlistor... Färdig
W: Duplicate sources.list entry [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages (/var/lib/apt/lists/download.tuxfamily.org_syzygy42_dists_gutsy_avant-window-navigator_binary-i386_Packages)
W: Du kan möjligen rätta till problemet genom att köra "apt-get update"
Läser paketlistor... Färdig
Bygger beroendeträd
Läser tillståndsinformation... Färdig
Följande paket kommer att uppgraderas:
  tzdata
1 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.
Behöver hämta 651kB arkiv.
Efter uppackning kommer ytterligare 0B utrymme användas på disken.
Vill du fortsätta [J/n]? j
Läs:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main tzdata 2007k-0ubuntu0.7.10 [651kB]
Hämtade 651kB på 25s (25,6kB/s)
Förkonfigurerar paket ...
(Läser databasen ... 102486 filer och kataloger installerade.)
Förbereder att ersätta tzdata 2007j-0ubuntu0.7.10 (med .../tzdata_2007k-0ubuntu0.7.10_all.deb) ...
Packar upp ersättande tzdata ...
Ställer in tzdata (2007k-0ubuntu0.7.10) ...

Current default timezone: 'Europe/Stockholm'
Local time is now:      Tue Jan  1 21:59:47 CET 2008.
Universal Time is now:  Tue Jan  1 20:59:47 UTC 2008.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


joel@Kissedesigns-2c:~$   

Well, running the remove and install ubuntu desktop then...

---

### Post by jamaisvu on 2008-01-01
> **~LoKe said:**
> Try...
```
sudo apt-get install ubuntu-desktop gnome-desktop-environment
```

[FONT=Franklin Gothic Medium]The ubuntu-desktop package includes GNOME.[/FONT]

---

### Post by ~LoKe on 2008-01-01
Swedish is not a language I'm familiar with, but I see no errors.  Installing those two packages I mentioned should restore things.

---

### Post by ~LoKe on 2008-01-01
> **jamaisvu said:**
> [FONT=Franklin Gothic Medium]The ubuntu-desktop package includes GNOME.[/FONT]

I figured it did but just wanted to make sure.

---

### Post by Dojan5 on 2008-01-01
It did come up with some interesting problems...
 > joel@Kissedesigns-2c:~$  sudo apt-get autoremove ubuntu-desktop
Läser paketlistor... Färdig
Bygger beroendeträd
Läser tillståndsinformation... Färdig
Paketet ubuntu-desktop är inte installerat, så det tas inte bort
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  libpopt-dev libsm-dev libmono-security1.0-cil libice-dev libgnutlsxx13
  libtasn1-3-dev libxine1-x libmono-sharpzip0.84-cil libgpg-error-dev
  mplayer-skins x11proto-xinerama-dev libsvga1 fftw3 libpango1.0-dev
  libmono-system-web1.0-cil libopencdk8-dev libhal-storage-dev
  x11proto-render-dev libgcrypt11-dev cdda2wav libxcb-xv0 libxi-dev
  libxrender-dev libcairo2-dev libsgutils1 libmono-cairo2.0-cil
  x11proto-composite-dev libxcursor-dev boo libbonobo2-dev python-compizconfig
  libggi2 libgnutls-dev ogmtools x11proto-randr-dev x11proto-damage-dev
  libgii1 libtaglib2.0-cil libxcb-shape0 libmono1.0-cil libxdamage-dev
  libmono-data-tds1.0-cil libxml2-dev libtunepimp5 libifp4
  libmono-system-data1.0-cil libesd0-dev libgii1-target-x x11proto-fixes-dev
  recordmydesktop libdvdnav4 vpnc sox libipoddevice0 libgnomevfs2-dev
  libxcomposite-dev libhal-dev libmozjs0d liblzo2-dev libxrandr-dev libxvmc1
  mpg123 libgconf2-dev libselinux1-dev libxft-dev openvpn mkvtoolnix
  libxfixes-dev libgnome2-dev libavahi-glib-dev libimlib2 libxcb-shm0
  libxinerama-dev libsepol1-dev libebml0 libmatroska0 libnjb5 libofa0
  libxine1-console libungif4g
Följande paket kommer att TAS BORT:
  boo cdda2wav fftw3 libavahi-glib-dev libbonobo2-dev libcairo2-dev libdvdnav4
  libebml0 libesd0-dev libgconf2-dev libgcrypt11-dev libggi2 libgii1
  libgii1-target-x libgnome2-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13
  libgpg-error-dev libhal-dev libhal-storage-dev libice-dev libifp4 libimlib2
  libipoddevice0 liblzo2-dev libmatroska0 libmono-cairo2.0-cil
  libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil
  libmono-system-data1.0-cil libmono-system-web1.0-cil libmono1.0-cil
  libmozjs0d libnjb5 libofa0 libopencdk8-dev libpango1.0-dev libpopt-dev
  libselinux1-dev libsepol1-dev libsgutils1 libsm-dev libsvga1
  libtaglib2.0-cil libtasn1-3-dev libtunepimp5 libungif4g libxcb-shape0
  libxcb-shm0 libxcb-xv0 libxcomposite-dev libxcursor-dev libxdamage-dev
  libxfixes-dev libxft-dev libxi-dev libxine1-console libxine1-x
  libxinerama-dev libxml2-dev libxrandr-dev libxrender-dev libxvmc1 mkvtoolnix
  mpg123 mplayer-skins ogmtools openvpn python-compizconfig recordmydesktop
  sox vpnc x11proto-composite-dev x11proto-damage-dev x11proto-fixes-dev
  x11proto-randr-dev x11proto-render-dev x11proto-xinerama-dev
0 uppgraderade, 0 nyinstallerade, 80 att ta bort och 0 ej uppgraderade.
Behöver hämta 0B arkiv.
Efter uppackning kommer 44,1MB att frigöras på disken.
Vill du fortsätta [J/n]? j
(Läser databasen ... 102484 filer och kataloger installerade.)
Tar bort boo ...
Tar bort cdda2wav ...
Tar bort libtunepimp5 ...
Tar bort libofa0 ...
Tar bort fftw3 ...
Tar bort libgnome2-dev ...
Tar bort libgnomevfs2-dev ...
Tar bort libavahi-glib-dev ...
Tar bort libbonobo2-dev ...
Tar bort libpango1.0-dev ...
Tar bort libcairo2-dev ...
Tar bort libdvdnav4 ...
Tar bort mkvtoolnix ...
Tar bort libmatroska0 ...
Tar bort libebml0 ...
Tar bort libesd0-dev ...
Tar bort libgconf2-dev ...
Tar bort libgnutls-dev ...
Tar bort libopencdk8-dev ...
Tar bort libgcrypt11-dev ...
Tar bort libggi2 ...
Tar bort libgii1 ...
Tar bort libgii1-target-x ...
Tar bort libgnutlsxx13 ...
Tar bort libgpg-error-dev ...
Tar bort libhal-storage-dev ...
Tar bort libhal-dev ...
Tar bort libsm-dev ...
Tar bort libice-dev ...
Tar bort libifp4 ...
Tar bort libimlib2 ...
Tar bort libipoddevice0 ...
Tar bort liblzo2-dev ...
Tar bort libmono-cairo2.0-cil ...
Tar bort libmono1.0-cil ...
Tar bort libmono-system-web1.0-cil ...
Tar bort libmono-system-data1.0-cil ...
Tar bort libmono-data-tds1.0-cil ...
Tar bort libmono-security1.0-cil ...
Tar bort libmono-sharpzip0.84-cil ...
Tar bort libmozjs0d ...
Tar bort libnjb5 ...
Tar bort libpopt-dev ...
Tar bort libselinux1-dev ...
Tar bort libsepol1-dev ...
Tar bort libsgutils1 ...
Tar bort libsvga1 ...
Tar bort libtaglib2.0-cil ...
Removing libtaglib2.0-cil from Mono
Tar bort libtasn1-3-dev ...
Tar bort libungif4g ...
Tar bort libxine1-x ...
Tar bort libxcb-shape0 ...
Tar bort libxcb-shm0 ...
Tar bort libxcb-xv0 ...
Tar bort libxcomposite-dev ...
Tar bort libxcursor-dev ...
Tar bort libxdamage-dev ...
Tar bort libxfixes-dev ...
Tar bort libxft-dev ...
Tar bort libxi-dev ...
Tar bort libxine1-console ...
Tar bort libxinerama-dev ...
Tar bort libxml2-dev ...
Tar bort libxrandr-dev ...
Tar bort libxrender-dev ...
Tar bort libxvmc1 ...
Tar bort mpg123 ...
Tar bort mplayer-skins ...
Tar bort ogmtools ...
Tar bort openvpn ...
Stopping virtual private network daemon:.
Tar bort python-compizconfig ...
Tar bort recordmydesktop ...
Tar bort sox ...
Tar bort vpnc ...
Tar bort x11proto-composite-dev ...
Tar bort x11proto-damage-dev ...
Tar bort x11proto-fixes-dev ...
Tar bort x11proto-randr-dev ...
Tar bort x11proto-render-dev ...
Tar bort x11proto-xinerama-dev ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
joel@Kissedesigns-2c:~$ sudo apt-get install ubuntu-desktop
Läser paketlistor... Färdig
Bygger beroendeträd
Läser tillståndsinformation... Färdig
Några paket kunde inte installeras. Det kan betyda att du har begärt
en omöjlig situation eller, om du använder den instabila utgåvan
att några nödvändiga paket ännu inte har skapats eller flyttats
ut från "Incoming".

Eftersom du bad om en enda handling är det mycket troligt att paketet
helt enkelt inte kan installeras och att en felrapport om detta bör
skickas in.
Följande information kan vara till hjälp för att lösa situationen:

Följande paket har beroenden som inte kan tillfredsställas:
  ubuntu-desktop: Beroende av: alacarte men det kommer inte att installeras
                  Beroende av: eog men det kommer inte att installeras
                  Beroende av: evince men det kommer inte att installeras
                  Beroende av: evolution-webcal men det kommer inte att installe
ras
                  Beroende av: fast-user-switch-applet men det kommer inte att i
nstalleras
                  Beroende av: file-roller men det kommer inte att installeras
                  Beroende av: gcalctool men det kommer inte att installeras
                  Beroende av: gconf-editor men det kommer inte att installeras
                  Beroende av: gdebi men det kommer inte att installeras
                  Beroende av: gdm men det kommer inte att installeras
                  Beroende av: gedit men det kommer inte att installeras
                  Beroende av: gimp-python men det kommer inte att installeras
                  Beroende av: gnome-about men det kommer inte att installeras
                  Beroende av: gnome-app-install men det kommer inte att install
eras
                  Beroende av: gnome-applets men det kommer inte att installeras
                  Beroende av: gnome-btdownload men det kommer inte att installe
ras
                  Beroende av: gnome-control-center men det kommer inte att inst
alleras
                  Beroende av: gnome-icon-theme men det kommer inte att installe
ras
                  Beroende av: gnome-keyring-manager men det kommer inte att ins
talleras
                  Beroende av: gnome-media men det kommer inte att installeras
                  Beroende av: gnome-menus men det kommer inte att installeras
                  Beroende av: gnome-netstatus-applet men det kommer inte att in
stalleras
                  Beroende av: gnome-nettool men det kommer inte att installeras
                  Beroende av: gnome-panel men det kommer inte att installeras
                  Beroende av: gnome-pilot-conduits men det kommer inte att inst
alleras
                  Beroende av: gnome-power-manager men det kommer inte att insta
lleras
                  Beroende av: gnome-session men det kommer inte att installeras
                  Beroende av: gnome-spell men det kommer inte att installeras
                  Beroende av: gnome-system-monitor men det kommer inte att inst
alleras
                  Beroende av: gnome-system-tools men det kommer inte att instal
leras
                  Beroende av: gnome-terminal men det kommer inte att installera
s
                  Beroende av: gnome-themes men det kommer inte att installeras
                  Beroende av: gnome-utils men det kommer inte att installeras
                  Beroende av: gnome-volume-manager men det kommer inte att inst
alleras
                  Beroende av: gthumb men det kommer inte att installeras
                  Beroende av: gtk2-engines men det kommer inte att installeras
                  Beroende av: gtk2-engines-pixbuf men det kommer inte att insta
lleras
                  Beroende av: gucharmap men det kommer inte att installeras
                  Beroende av: hal-device-manager men det kommer inte att instal
leras
                  Beroende av: hwdb-client-gnome men det kommer inte att install
eras
                  Beroende av: language-selector men det kommer inte att install
eras
                  Beroende av: libgnome2-perl men det kommer inte att installera
s
                  Beroende av: metacity men det kommer inte att installeras
                  Beroende av: nautilus men det kommer inte att installeras
                  Beroende av: nautilus-cd-burner men det kommer inte att instal
leras
                  Beroende av: nautilus-sendto men det kommer inte att installer
as
                  Beroende av: notification-daemon men det kommer inte att insta
lleras
                  Beroende av: screensaver-default-images men det kommer inte at
t installeras
                  Beroende av: serpentine men det kommer inte att installeras
                  Beroende av: sound-juicer men det kommer inte att installeras
                  Beroende av: ssh-askpass-gnome men det kommer inte att install
eras
                  Beroende av: synaptic men det kommer inte att installeras
                  Beroende av: system-config-printer men det kommer inte att ins
talleras
                  Beroende av: tangerine-icon-theme men det kommer inte att inst
alleras
                  Beroende av: tsclient men det kommer inte att installeras
                  Beroende av: ubuntu-artwork men det kommer inte att installera
s
                  Beroende av: update-notifier men det kommer inte att installer
as
                  Beroende av: vino men det kommer inte att installeras
                  Beroende av: xdg-user-dirs-gtk men det kommer inte att install
eras
                  Beroende av: xscreensaver-data men det kommer inte att install
eras
                  Beroende av: xscreensaver-gl men det kommer inte att installer
as
                  Beroende av: yelp men det kommer inte att installeras
                  Beroende av: zenity men det kommer inte att installeras
                  Rekommenderar: apport-gtk men det kommer inte att installeras
                  Rekommenderar: bluez-gnome men det kommer inte att installeras
                  Rekommenderar: brltty-x11 men det kommer inte att installeras
                  Rekommenderar: bug-buddy men det kommer inte att installeras
                  Rekommenderar: compiz men det kommer inte att installeras
                  Rekommenderar: contact-lookup-applet men det kommer inte att i
nstalleras
                  Rekommenderar: deskbar-applet men det kommer inte att installe
ras
                  Rekommenderar: displayconfig-gtk men det kommer inte att insta
lleras
                  Rekommenderar: ekiga men det kommer inte att installeras
                  Rekommenderar: evolution men det kommer inte att installeras
                  Rekommenderar: evolution-exchange men det kommer inte att inst
alleras
                  Rekommenderar: evolution-plugins men det kommer inte att insta
lleras
                  Rekommenderar: f-spot men det kommer inte att installeras
                  Rekommenderar: firefox men det kommer inte att installeras
                  Rekommenderar: firefox-gnome-support men det kommer inte att i
nstalleras
                  Rekommenderar: gimp men det kommer inte att installeras
                  Rekommenderar: gimp-print men det kommer inte att installeras
                  Rekommenderar: gnome-accessibility-themes men det kommer inte
att installeras
                  Rekommenderar: gnome-games men det kommer inte att installeras
                  Rekommenderar: gnome-mag men det kommer inte att installeras
                  Rekommenderar: gnome-orca men det kommer inte att installeras
                  Rekommenderar: gnome-screensaver men det kommer inte att insta
lleras
                  Rekommenderar: gnome-user-guide men det kommer inte att instal
leras
                  Rekommenderar: hal-cups-utils men det kommer inte att installe
ras
                  Rekommenderar: libdeskbar-tracker men det kommer inte att inst
alleras
                  Rekommenderar: network-manager-gnome men det kommer inte att i
nstalleras
                  Rekommenderar: onboard men det kommer inte att installeras
                  Rekommenderar: openoffice.org men det kommer inte att installe
ras
                  Rekommenderar: openoffice.org-evolution men det kommer inte at
t installeras
                  Rekommenderar: openoffice.org-gnome men det kommer inte att in                                                          stalleras
                  Rekommenderar: pidgin men det kommer inte att installeras
                  Rekommenderar: restricted-manager men det kommer inte att inst                                                          alleras
                  Rekommenderar: rhythmbox men det kommer inte att installeras
                  Rekommenderar: scim men det kommer inte att installeras
                  Rekommenderar: scim-gtk2-immodule men det kommer inte att inst                                                          alleras
                  Rekommenderar: scim-tables-additional men det kommer inte att                                                           installeras
                  Rekommenderar: tomboy men det kommer inte att installeras
                  Rekommenderar: totem men det kommer inte att installeras
                  Rekommenderar: totem-mozilla men det kommer inte att installer                                                          as
                  Rekommenderar: tracker men det kommer inte att installeras
                  Rekommenderar: tracker-search-tool men det kommer inte att ins                                                          talleras
                  Rekommenderar: ubufox men det kommer inte att installeras
                  Rekommenderar: ubuntu-docs men det kommer inte att installeras
                  Rekommenderar: xsane men det kommer inte att installeras
E: Trasiga paket
joel@Kissedesigns-2c:~$


What the last part say, after the install GNOME desktop is
Beroende means like Need, like                   "Beroende av: file-roller men det kommer inte att installeras" Means Need: file-roller but it wont be installed...
Then it say a lot of Rekommenderar which means Recommends like
                  "Rekommenderar: ubufox men det kommer inte att installeras" means "Recommends ubufox but it wont be installed....
This is some "interesting" error....
Seriously, it feels uncomfortable, i have some VERY important files on the drive...

---

### Post by ~LoKe on 2008-01-01
Uhm...please be careful with what you type.  I never said autoremove, I said install...

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Dojan5 on 2008-01-01
> **~LoKe said:**
> Swedish is not a language I'm familiar with, but I see no errors.  Installing those two packages I mentioned should restore things.
Sorry, but bra means good...
Of what i can say it say everything succedeed...

[QUOTE=LoKe]
Uhm...please be careful with what you type. I never said autoremove, I said install...
 
 
```
:
sudo apt-get install ubuntu-desktop
```
[/QUOTE]
> E: Trasiga paket
I did that... I still get the same problem, the E: i think mean error: and trasiga paket means Broken Packages...

A little question...
Aint it just to reboot and insert the Ubuntu CD and repair????

---

### Post by MalfunctioningMartian on 2008-01-01
Just an idea, if you are scared about losing files why not boot with a live cd and back them up to a flash drive?

---

### Post by Dojan5 on 2008-01-01
FlashDrive like, umm, my Mp3???
N, i dont have enough memory on it to store all the files, and, there is a problem with my motherboard, else i would have two harddrives and two cd readers (a burner too)
But, i cant use that anymoe since, umm, well, there was some problem with the motherboard and something... Gah, im 14 cant remember all the technical stuff... :S
Thanks for the tip anyway ^_^

===EDIT===
Hey cool!
I can access the whole filesystem through KDE!!!

---

### Post by jamaisvu on 2008-01-01
> **Dojan5 said:**
> What the last part say, after the install GNOME desktop is
Beroende means like Need, like                   "Beroende av: file-roller men det kommer inte att installeras" Means Need: file-roller but it wont be installed...
Then it say a lot of Rekommenderar which means Recommends like
                  "Rekommenderar: ubufox men det kommer inte att installeras" means "Recommends ubufox but it wont be installed....
This is some "interesting" error....

Okay, so you have a clean install of GNOME, and you want two more packages, so:

[FONT=Courier New]sudo apt-get install file-roller ubufox
[/FONT]
> Seriously, it feels uncomfortable, i have some VERY important files on the drive...

Programs you add and remove are in /bin/, /usr/ and /opt/ -- they don't touch /home/, where your data live!

---

### Post by Dojan5 on 2008-01-01
OH! Found something i missed before...
```
Läser paketlistor... Färdig
 Bygger beroendeträd
 Läser tillståndsinformation... Färdig
 Några paket kunde inte installeras. Det kan betyda att du har begärt
 en omöjlig situation eller, om du använder den instabila utgåvan
 att några nödvändiga paket ännu inte har skapats eller flyttats
 ut från "Incoming".

Eftersom du bad om en enda handling är det mycket troligt att paketet
 helt enkelt inte kan installeras och att en felrapport om detta bör
 skickas in.
 Följande information kan vara till hjälp för att lösa situationen:
```


```
Reading packages... Done
Builds nessesary trees
Reading eh, something information... Done
Some packages could not be installed. It can mean that you asked for a impossible action or, if you use the instable build that some nessecary packages not yet have been created or moved out from "incoming"

Since you asked of one single action it is most likely that the package simply cannot be installed and that an error report about this should send in,

Following information can be useful to solve the problem
```
It dont really say solve the problem, it say solve the situation or clear up the situation, but i dont find that really nessecary, but i commented that to...

---

### Post by Dojan5 on 2008-01-01
> **jamaisvu said:**
> Okay, so you have a clean install of GNOME, and you want two more packages, so:

[FONT=Courier New]sudo apt-get install file-roller ubufox
[/FONT]


Programs you add and remove are in /bin/, /usr/ and /opt/ -- they don't touch /home/, where your data live!

Nononono, it is just an example, i dont have GNOME...
It was just an example of what it means...

---

### Post by Dojan5 on 2008-01-01
Noone?

---

### Post by knutschr on 2008-01-01
I just wander:
Could trying
```
sudo apt-get install -f ubuntu-desktop
```
do any harm? Anybody knows?

---

### Post by Dojan5 on 2008-01-01
> **knutschr said:**
> I just wander:
Could trying
```
sudo apt-get install -f ubuntu-desktop
```
do any harm? Anybody knows?

Dunno, dont think ill know in a while til i do same big mistake...
Im doing something confidential, i may not tell and im backing up all the files...
Im going to reinstall Windows XP Pro sp2 and then Dual Boot with Ubuntu Gutsy...
Any good huide for it?
And yaa, i can back up, i had to open up the computer and switch out the cd driver with a cd burner... Luckily it works...
Thank all of you for helping me, though, the problem is still unsolved, i can use the computer til i install XP on it...
Thanks again!
Yours sincerely
Joel L

---

### Post by ~LoKe on 2008-01-01
Hold on, hold on.  Your computer isn't hosed or anything.  You can still log into kde, and that's a plus.  Let's try a few things.  Log into KDE, open up Konsole.  Type the following
```
sudo dpkg -r gnome-desktop-environment
```
If that removes a package, then proceed:
```
sudo aptitude install gnome-desktop-environment
```

---

### Post by Dojan5 on 2008-01-02
> **~LoKe said:**
> Hold on, hold on.  Your computer isn't hosed or anything.  You can still log into kde, and that's a plus.  Let's try a few things.  Log into KDE, open up Konsole.  Type the following
```
sudo dpkg -r gnome-desktop-environment
```
If that removes a package, then proceed:
```
sudo aptitude install gnome-desktop-environment
```

You solved it, the first thing was something about remove GNOME, and it ignored it.
The second thing acctually worked.
But i have realized that i NEED to dual boot Win XP and Ubuntu.
So, with my backups done and my XP cd im just going to find a dual boot guide....
Cya laters!!!

---

### Post by ~LoKe on 2008-01-02
Happy to have helped!  Sorry it took so long. ;)

---

