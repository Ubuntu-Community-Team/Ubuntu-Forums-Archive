---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-06-12
forum: General Help
---

### Post by andubu on 2017-06-12
hi

so i have a problem... 
i've make something realy wrong:?
i've i try to install any package in the terminal i get this output: 
root@ubu:/home/ubu# apt upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Paketaktualisierung (Upgrade) wird berechnet... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
6 nicht vollständig installiert oder entfernt.
Es müssen 58.6 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] j
Holen:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main i386 linux-image-4.10.0-20-generic i386 4.10.0-20.22 [21.8 MB]
Holen:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty-updates/main i386 linux-image-extra-4.10.0-20-generic i386 4.10.0-20.22 [36.8 MB]
Es wurden 58.6 MB in 39 s geholt (1'492 kB/s).                                 
linux-image-4.10.0-22-generic (4.10.0-22.24) wird eingerichtet ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.10.0-22-generic
) points to /boot/initrd.img-4.10.0-22-generic
 (/boot/initrd.img-4.10.0-22-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.10.0-22-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.10.0-22-generic
) points to /boot/vmlinuz-4.10.0-22-generic
 (/boot/vmlinuz-4.10.0-22-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.10.0-22-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-22-generic /boot/vmlinuz-4.10.0-22-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.10.0-22-generic /boot/vmlinuz-4.10.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-22-generic /boot/vmlinuz-4.10.0-22-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.10.0-22-generic /boot/vmlinuz-4.10.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.10.0-22-generic /boot/vmlinuz-4.10.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.10.0-22-generic /boot/vmlinuz-4.10.0-22-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: net.ifnames=0: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.10.0-22-generic.postinst line 1052.
dpkg: Fehler beim Bearbeiten des Paketes linux-image-4.10.0-22-generic (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 2 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-image-extra-4.10.0-22-generic:
 linux-image-extra-4.10.0-22-generic hängt ab von linux-image-4.10.0-22-generic; aber:
  Paket linux-image-4.10.0-22-generic ist noch nicht konfiguriert.


dpkg: Fehler beim Bearbeiten des Paketes linux-image-extra-4.10.0-22-generic (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-image-generic:
 linux-image-generic hängt ab von linux-image-4.10.0-22-generic; aber:
  Paket linux-image-4.10.0-22-generic ist noch nicht konfiguriert.
 linux-imEs wurde kein Apport-Bericht verfasst, da die Fehlermeldung darauf hindeutet, dass dies lediglich ein Folgefehler eines vorherigen Problems ist.
                                                                         Es wurde kein Apport-Bericht verfasst, da die Fehlermeldung darauf hindeutet, dass dies lediglich ein Folgefehler eines vorherigen Problems ist.
                                                         Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist.
                                                             age-generic hängt ab von linux-image-extra-4.10.0-22-generic; aber:
  Paket linux-image-extra-4.10.0-22-generic ist noch nicht konfiguriert.


dpkg: Fehler beim Bearbeiten des Paketes linux-image-generic (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-generic:
 linux-generic hängt ab von linux-image-generic (= 4.10.0.22.24); aber:
  Paket linux-image-generic ist noch nicht konfiguriert.


dpkg: Fehler beim Bearbeiten des Paketes linux-generic (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 linux-image-4.10.0-22-generic
 linux-image-extra-4.10.0-22-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubu:/home/ubu# 

sry for bad english

and thanks for help

---

