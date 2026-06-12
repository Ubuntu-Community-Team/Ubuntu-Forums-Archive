---
title: "libssl1.0.0:amd64 isn't configured (Ubuntu 16.04 LTS)"
date: 2017-06-10
forum: General Help
---

### Post by albertxe on 2017-06-10
Hi:

I'm a relatively new Ubuntu user (Ubuntu 16.04 LTS)
I'm having problems with the installation of clamAV antivirus and I suposed that I can have the same problems when I tray to install other programs.
A message in the Terminal tell me that "libssl1.0.0:amd64" isn't configured and because of it there are some errors and I'm not able to update the antivirus database.
Maybe it could be because of Wine of the programs that I installed with it.

I've copied here the message that appears in the Terminal, but I'm Basque and I configured Ubuntu in Basque. So some of the sentences are in Basque (unfortunatelly, not all the messages or help in Ubuntu is still translated in Basque)

> 

alberto@alberto-Lenovo-B50-50:~$ sudo apt-get install clamav clamav-daemon
Pakete Zerrenda irakurtzen... Eginda
Dependentzia zuhaitza eraikitzen       
Egoera argibideak irakurtzen... Eginda
The following additional packages will be installed:
  clamav-base clamav-freshclam clamdscan libclamav7 libllvm3.6v5
Iradokitako paketeak:
  clamav-docs daemon libclamunrar7
Ondorengo pakete BERRIAK instalatuko dira:
  clamav clamav-base clamav-daemon clamav-freshclam clamdscan libclamav7
  libllvm3.6v5
0 bertsio berritua(k), 7 berriki instalatuta, 0 kentzeko, eta 0 bertsio-berritu gabe.
5 ez erabat instalatuta edo kenduta.
Artxiboetako 9378 kB eskuratu behar dira.
Ekintza honen ondoren, 38,2 MB gehiago erabiliko dira diskoan.
Aurrera jarraitu nahi al duzu? [B/e] B
Hartu:1 [http://de2.archive.ubuntu.com/ubuntu](http://de2.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 clamav-base all 0.99.2+dfsg-0ubuntu0.16.04.1 [58,4 kB]
Hartu:2 [http://de2.archive.ubuntu.com/ubuntu](http://de2.archive.ubuntu.com/ubuntu) xenial/main amd64 libllvm3.6v5 amd64 1:3.6.2-3ubuntu2 [8075 kB]
Hartu:3 [http://de2.archive.ubuntu.com/ubuntu](http://de2.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libclamav7 amd64 0.99.2+dfsg-0ubuntu0.16.04.1 [762 kB]
Hartu:4 [http://de2.archive.ubuntu.com/ubuntu](http://de2.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 clamav-freshclam amd64 0.99.2+dfsg-0ubuntu0.16.04.1 [115 kB]
Hartu:5 [http://de2.archive.ubuntu.com/ubuntu](http://de2.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 clamav amd64 0.99.2+dfsg-0ubuntu0.16.04.1 [98,5 kB]
Hartu:6 [http://de2.archive.ubuntu.com/ubuntu](http://de2.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 clamav-daemon amd64 0.99.2+dfsg-0ubuntu0.16.04.1 [196 kB]
Hartu:7 [http://de2.archive.ubuntu.com/ubuntu](http://de2.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 clamdscan amd64 0.99.2+dfsg-0ubuntu0.16.04.1 [74,2 kB]
Lortuta: 9378 kB (30s) (310 kB/s)                                              
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Aurrez desautatutako clamav-base paketea hautatzen.
(Datu-basea irakurtzen ... 283377 fitxategi edo direktorio daude unean instalatuta).
.../clamav-base_0.99.2+dfsg-0ubuntu0.16.04.1_all.deb deskonprimitzeko prestatzen...
clamav-base (0.99.2+dfsg-0ubuntu0.16.04.1) deskonprimitzen...
Aurrez desautatutako libllvm3.6v5:amd64 paketea hautatzen.
.../libllvm3.6v5_1%3a3.6.2-3ubuntu2_amd64.deb deskonprimitzeko prestatzen...
libllvm3.6v5:amd64 (1:3.6.2-3ubuntu2) deskonprimitzen...
Aurrez desautatutako libclamav7 paketea hautatzen.
.../libclamav7_0.99.2+dfsg-0ubuntu0.16.04.1_amd64.deb deskonprimitzeko prestatzen...
libclamav7 (0.99.2+dfsg-0ubuntu0.16.04.1) deskonprimitzen...
Aurrez desautatutako clamav-freshclam paketea hautatzen.
.../clamav-freshclam_0.99.2+dfsg-0ubuntu0.16.04.1_amd64.deb deskonprimitzeko prestatzen...
clamav-freshclam (0.99.2+dfsg-0ubuntu0.16.04.1) deskonprimitzen...
Aurrez desautatutako clamav paketea hautatzen.
.../clamav_0.99.2+dfsg-0ubuntu0.16.04.1_amd64.deb deskonprimitzeko prestatzen...
clamav (0.99.2+dfsg-0ubuntu0.16.04.1) deskonprimitzen...
Aurrez desautatutako clamav-daemon paketea hautatzen.
.../clamav-daemon_0.99.2+dfsg-0ubuntu0.16.04.1_amd64.deb deskonprimitzeko prestatzen...
clamav-daemon (0.99.2+dfsg-0ubuntu0.16.04.1) deskonprimitzen...
Aurrez desautatutako clamdscan paketea hautatzen.
.../clamdscan_0.99.2+dfsg-0ubuntu0.16.04.1_amd64.deb deskonprimitzeko prestatzen...
clamdscan (0.99.2+dfsg-0ubuntu0.16.04.1) deskonprimitzen...
libc-bin (2.23-0ubuntu7)-(r)en abiarazleak prozesatzen ...
man-db (2.7.5-1)-(r)en abiarazleak prozesatzen ...
systemd (229-4ubuntu17)-(r)en abiarazleak prozesatzen ...
ureadahead (0.100.0-19)-(r)en abiarazleak prozesatzen ...
ureadahead will be reprofiled on next reboot
libssl1.0.0:amd64 (1.0.2g-1ubuntu4.8) konfiguratzen...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: errorea libssl1.0.0:amd64 paketea prozesatzean (--configure):
 post-installation script-a instalatuta azpiprozesuak 1 errorea eman du irteeran
libssl1.0.0:i386 (1.0.2g-1ubuntu4.8) konfiguratzen...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: errorea libssl1.0.0:i386 paketea prozesatzean (--configure):
 post-installation script-a instalatuta azpiprozesuak 1 errorea eman du irteeran
dpkg: ezin da libtorrent-rasterbar8 konfiguratu, mendekotasun arazoak direla eta:
 libtorrent-rasterbar8 honen mendekoa da: libssl1.0.0 (>= 1.0.1); nolanahi ere:
  libssl1.0.0:amd64 paketea ez dago konfiguratuta oraindik.

dpkg: errorea libtorrent-rasterbar8 paketea prozesatzean (--configure):
 mendekotasun arazoak - konfiguratu gabe uzten ari da
dpkg: ezin da openssl konfiguratu, mendekotasun arazoak direla eta:
 openssl honen mendekoa da: libssl1.0.0 (>= 1.0.2g); nolanahi ere:
  libssl1.0.0:amd64 paketea ez dago konfiguratuta oraindik.

dpkg: errorea openssl paketea prozesatzean (--configure):
 mendekotasun arazoak - konfiguratu gabe uzten ari da
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because MaxReports has already been reached
                dpkg: ezin da qbittorrent konfiguratu, mendekotasun arazoak direla eta:
 qbittorrent honen mendekoa da: libtorrent-rasterbar8 (>= 1.0.11+git20172003.8736a59adc); nolanahi ere:
  libtorrent-rasterbar8 paketea ez dago konfiguratuta oraindik.

dpkg: errorea qbittorrent paketea prozesatzean (--configure):
 mendekotasun arazoak - konfiguratu gabe uzten ari da
clamav-base (0.99.2+dfsg-0ubuntu0.16.04.1) konfiguratzen...
No apport report written because MaxReports has already been reached
                                                                    libllvm3.6v5:amd64 (1:3.6.2-3ubuntu2) konfiguratzen...
dpkg: ezin da libclamav7 konfiguratu, mendekotasun arazoak direla eta:
 libclamav7 honen mendekoa da: libssl1.0.0 (>= 1.0.0); nolanahi ere:
  libssl1.0.0:amd64 paketea ez dago konfiguratuta oraindik.

dpkg: errorea libclamav7 paketea prozesatzean (--configure):
 mendekotasun arazoak - konfiguratu gabe uzten ari da
No apport report written because MaxReports has already been reached
                                                                    dpkg: ezin da clamav-freshclam konfiguratu, mendekotasun arazoak direla eta:
 clamav-freshclam honen mendekoa da: libclamav7 (>= 0.99~rc1); nolanahi ere:
  libclamav7 paketea ez dago konfiguratuta oraindik.
 clamav-freshclam honen mendekoa da: libssl1.0.0 (>= 1.0.0); nolanahi ere:
  libssl1.0.0:amd64 paketea ez dago konfiguratuta oraindik.

dpkg: errorea clamav-freshclam paketea prozesatzean (--configure):
 mendekotasun arazoak - konfiguratu gabe uzten ari da
No apport report written because MaxReports has already been reached
                                                                    dpkg: ezin da clamav konfiguratu, mendekotasun arazoak direla eta:
 clamav honen mendekoa da: clamav-freshclam (>= 0.99.2+dfsg) | clamav-data; nolanahi ere:
  clamav-freshclam paketea ez dago konfiguratuta oraindik.
  clamav-data paketea ez dago instalatuta.
  clamav-freshclam paketea, clamav-data hornitzen duena, oraindik ez dago konfiguratuta.
 clamav honen mendekoa da: libclamav7 (>= 0.99~rc1); nolanahi ere:
  libclamav7 paketea ez dago konfiguratuta oraindik.
 clamav honen mendekoa da: libssl1.0.0 (>= 1.0.0); nolanahi ere:
  libssl1.0.0:amd64 paketea ez dago konfiguratuta oraindik.

dpkg: errorea clamav paketea prozesatzean (--configure):
 mendekotasun arazoak - konfiguratu gabe uzten ari da
No apport report written because MaxReports has already been reached
                                                                    dpkg: ezin da clamav-daemon konfiguratu, mendekotasun arazoak direla eta:
 clamav-daemon honen mendekoa da: clamav-freshclam (>= 0.99.2+dfsg) | clamav-data; nolanahi ere:
  clamav-freshclam paketea ez dago konfiguratuta oraindik.
  clamav-data paketea ez dago instalatuta.
  clamav-freshclam paketea, clamav-data hornitzen duena, oraindik ez dago konfiguratuta.
 clamav-daemon honen mendekoa da: libclamav7 (>= 0.99~rc1); nolanahi ere:
  libclamav7 paketea ez dago konfiguratuta oraindik.
 clamav-daemon honen mendekoa da: libssl1.0.0 (>= 1.0.0); nolanahi ere:
  libssl1.0.0:amd64 paketea ez dago konfiguratuta oraindik.

dpkg: errorea clamav-daemon paketea prozesatzean (--configure):
 mendekotasun arazoak - konfiguratu gabe uzten ari da
No apport report written because MaxReports has already been reached
                                                                    dpkg: ezin da clamdscan konfiguratu, mendekotasun arazoak direla eta:
 clamdscan honen mendekoa da: libssl1.0.0 (>= 1.0.0); nolanahi ere:
  libssl1.0.0:amd64 paketea ez dago konfiguratuta oraindik.

dpkg: errorea clamdscan paketea prozesatzean (--configure):
 mendekotasun arazoak - konfiguratu gabe uzten ari da
No apport report written because MaxReports has already been reached
                                                                    libc-bin (2.23-0ubuntu7)-(r)en abiarazleak prozesatzen ...
Erroreak aurkitu dira prozesatzean:
 libssl1.0.0:amd64
 libssl1.0.0:i386
 libtorrent-rasterbar8
 openssl
 qbittorrent
 libclamav7
 clamav-freshclam
 clamav
 clamav-daemon
 clamdscan
E: Sub-process /usr/bin/dpkg returned an error code (1)
alberto@alberto-Lenovo-B50-50:~$ sudo freshclam
ERROR: Can't open/parse the config file /etc/clamav/freshclam.conf



What I can do? Thank you very much.

---

