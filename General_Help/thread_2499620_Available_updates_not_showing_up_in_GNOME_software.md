---
title: "Available updates not showing up in GNOME software"
date: 2024-08-04
forum: General Help
---

### Post by bingo90 on 2024-08-04
Listing  available updates with "apt update" and "apt list --upgradable" shows  that there are updates available, but they don't show up in GNOME  Software. Is there any way to fix this? The only additional plugin I  installed is the flatpak plugin.



The updates also show up in pkcon update.

---

### Post by #&amp;thj^% on 2024-08-04
Could you please offer us something here to help you with???
Show us those commands and the returns. Please we are not mind readers.

---

### Post by bingo90 on 2024-08-04
I mean, sure? I doubt it's gonna be of any use though - it's just the list of available updates...

apt list --upgradable:

```
Listing... Done
apparmor/noble-updates 4.0.1really4.0.0-beta3-0ubuntu0.1 amd64 [upgradable from: 4.0.0-beta3-0ubuntu3]
apport-core-dump-handler/noble-updates 2.28.1-0ubuntu3 all [upgradable from: 2.28.1-0ubuntu2]
apport-gtk/noble-updates 2.28.1-0ubuntu3 all [upgradable from: 2.28.1-0ubuntu2]
apport/noble-updates 2.28.1-0ubuntu3 all [upgradable from: 2.28.1-0ubuntu2]
cloud-init/noble-updates 24.1.3-0ubuntu3.3 all [upgradable from: 24.1.3-0ubuntu3]
dhcpcd-base/noble-updates 1:10.0.6-1ubuntu3.1 amd64 [upgradable from: 1:10.0.6-1ubuntu3]
dracut-install/noble-updates 060+5-1ubuntu3.2 amd64 [upgradable from: 060+5-1ubuntu3]
evolution-data-server-common/noble-updates 3.52.3-0ubuntu1 all [upgradable from: 3.52.0-1build3]
evolution-data-server/noble-updates 3.52.3-0ubuntu1 amd64 [upgradable from: 3.52.0-1build3]
gir1.2-javascriptcoregtk-4.1/noble-updates 2.44.2-0ubuntu0.24.04.2 amd64 [upgradable from: 2.44.2-0ubuntu0.24.04.1]
gir1.2-javascriptcoregtk-6.0/noble-updates 2.44.2-0ubuntu0.24.04.2 amd64 [upgradable from: 2.44.2-0ubuntu0.24.04.1]
gir1.2-mutter-14/noble-updates 46.2-1ubuntu0.24.04.1 amd64 [upgradable from: 46.0-1ubuntu9]
gir1.2-webkit-6.0/noble-updates 2.44.2-0ubuntu0.24.04.2 amd64 [upgradable from: 2.44.2-0ubuntu0.24.04.1]
gir1.2-webkit2-4.1/noble-updates 2.44.2-0ubuntu0.24.04.2 amd64 [upgradable from: 2.44.2-0ubuntu0.24.04.1]
gnome-calculator/noble-updates 1:46.1-1ubuntu1~24.04.1 amd64 [upgradable from: 1:46.0-1ubuntu1]
gnome-shell-common/noble-updates 46.0-0ubuntu6~24.04.1 all [upgradable from: 46.0-0ubuntu5.1]
gnome-shell-extension-appindicator/noble-updates 58-1 all [upgradable from: 57-2]
gnome-shell-extension-ubuntu-tiling-assistant/noble-updates 46-1ubuntu1.1 all [upgradable from: 46-1ubuntu1]
gnome-shell/noble-updates 46.0-0ubuntu6~24.04.1 amd64 [upgradable from: 46.0-0ubuntu5.1]
gnome-text-editor/noble-updates 46.3-0ubuntu1 amd64 [upgradable from: 46.1-1]
gstreamer1.0-pipewire/noble-updates 1.0.5-1ubuntu1 amd64 [upgradable from: 1.0.5-1]
initramfs-tools-bin/noble-updates 0.142ubuntu25.1 amd64 [upgradable from: 0.142ubuntu25]
initramfs-tools-core/noble-updates 0.142ubuntu25.1 all [upgradable from: 0.142ubuntu25]
initramfs-tools/noble-updates 0.142ubuntu25.1 all [upgradable from: 0.142ubuntu25]
libapparmor1/noble-updates 4.0.1really4.0.0-beta3-0ubuntu0.1 amd64 [upgradable from: 4.0.0-beta3-0ubuntu3]
libcamel-1.2-64t64/noble-updates 3.52.3-0ubuntu1 amd64 [upgradable from: 3.52.0-1build3]
libebackend-1.2-11t64/noble-updates 3.52.3-0ubuntu1 amd64 [upgradable from: 3.52.0-1build3]
libebook-1.2-21t64/noble-updates 3.52.3-0ubuntu1 amd64 [upgradable from: 3.52.0-1build3]
libebook-contacts-1.2-4t64/noble-updates 3.52.3-0ubuntu1 amd64 [upgradable from: 3.52.0-1build3]
libecal-2.0-3/noble-updates 3.52.3-0ubuntu1 amd64 [upgradable from: 3.52.0-1build3]
libedata-book-1.2-27t64/noble-updates 3.52.3-0ubuntu1 amd64 [upgradable from: 3.52.0-1build3]
libedata-cal-2.0-2t64/noble-updates 3.52.3-0ubuntu1 amd64 [upgradable from: 3.52.0-1build3]
libedataserver-1.2-27t64/noble-updates 3.52.3-0ubuntu1 amd64 [upgradable from: 3.52.0-1build3]
libedataserverui-1.2-4t64/noble-updates 3.52.3-0ubuntu1 amd64 [upgradable from: 3.52.0-1build3]
libfprint-2-2/noble-updates 1:1.94.7+tod1-0ubuntu5~24.04.1 amd64 [upgradable from: 1:1.94.7+tod1-0ubuntu4]
libfprint-2-tod1/noble-updates 1:1.94.7+tod1-0ubuntu5~24.04.1 amd64 [upgradable from: 1:1.94.7+tod1-0ubuntu4]
libjavascriptcoregtk-4.1-0/noble-updates 2.44.2-0ubuntu0.24.04.2 amd64 [upgradable from: 2.44.2-0ubuntu0.24.04.1]
libjavascriptcoregtk-6.0-1/noble-updates 2.44.2-0ubuntu0.24.04.2 amd64 [upgradable from: 2.44.2-0ubuntu0.24.04.1]
libmutter-14-0/noble-updates 46.2-1ubuntu0.24.04.1 amd64 [upgradable from: 46.0-1ubuntu9]
libnautilus-extension4/noble-updates 1:46.2-0ubuntu0.2 amd64 [upgradable from: 1:46.0-0ubuntu2]
libnss-systemd/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
libpam-modules-bin/noble-updates 1.5.3-5ubuntu5.1 amd64 [upgradable from: 1.5.3-5ubuntu5]
libpam-modules/noble-updates 1.5.3-5ubuntu5.1 amd64 [upgradable from: 1.5.3-5ubuntu5]
libpam-runtime/noble-updates 1.5.3-5ubuntu5.1 all [upgradable from: 1.5.3-5ubuntu5]
libpam-systemd/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
libpam0g/noble-updates 1.5.3-5ubuntu5.1 amd64 [upgradable from: 1.5.3-5ubuntu5]
libpipewire-0.3-0t64/noble-updates 1.0.5-1ubuntu1 amd64 [upgradable from: 1.0.5-1]
libpipewire-0.3-common/noble-updates 1.0.5-1ubuntu1 all [upgradable from: 1.0.5-1]
libpipewire-0.3-modules/noble-updates 1.0.5-1ubuntu1 amd64 [upgradable from: 1.0.5-1]
libspa-0.2-bluetooth/noble-updates 1.0.5-1ubuntu1 amd64 [upgradable from: 1.0.5-1]
libspa-0.2-modules/noble-updates 1.0.5-1ubuntu1 amd64 [upgradable from: 1.0.5-1]
libsystemd-shared/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
libsystemd0/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
libudev1/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
libwebkit2gtk-4.1-0/noble-updates 2.44.2-0ubuntu0.24.04.2 amd64 [upgradable from: 2.44.2-0ubuntu0.24.04.1]
libwebkitgtk-6.0-4/noble-updates 2.44.2-0ubuntu0.24.04.2 amd64 [upgradable from: 2.44.2-0ubuntu0.24.04.1]
mutter-common-bin/noble-updates 46.2-1ubuntu0.24.04.1 amd64 [upgradable from: 46.0-1ubuntu9]
mutter-common/noble-updates 46.2-1ubuntu0.24.04.1 all [upgradable from: 46.0-1ubuntu9]
nautilus-data/noble-updates 1:46.2-0ubuntu0.2 all [upgradable from: 1:46.0-0ubuntu2]
nautilus/noble-updates 1:46.2-0ubuntu0.2 amd64 [upgradable from: 1:46.0-0ubuntu2]
pipewire-alsa/noble-updates 1.0.5-1ubuntu1 amd64 [upgradable from: 1.0.5-1]
pipewire-audio/noble-updates 1.0.5-1ubuntu1 all [upgradable from: 1.0.5-1]
pipewire-bin/noble-updates 1.0.5-1ubuntu1 amd64 [upgradable from: 1.0.5-1]
pipewire-pulse/noble-updates 1.0.5-1ubuntu1 amd64 [upgradable from: 1.0.5-1]
pipewire/noble-updates 1.0.5-1ubuntu1 amd64 [upgradable from: 1.0.5-1]
python3-apport/noble-updates 2.28.1-0ubuntu3 all [upgradable from: 2.28.1-0ubuntu2]
python3-distupgrade/noble-updates 1:24.04.19 all [upgradable from: 1:24.04.16]
python3-problem-report/noble-updates 2.28.1-0ubuntu3 all [upgradable from: 2.28.1-0ubuntu2]
systemd-dev/noble-updates 255.4-1ubuntu8.2 all [upgradable from: 255.4-1ubuntu8]
systemd-oomd/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
systemd-resolved/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
systemd-sysv/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
systemd-timesyncd/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
systemd/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
tzdata/noble-updates 2024a-3ubuntu1.1 all [upgradable from: 2024a-2ubuntu1]
ubuntu-pro-client-l10n/noble-updates 32.3.1~24.04 amd64 [upgradable from: 31.2.3]
ubuntu-pro-client/noble-updates 32.3.1~24.04 amd64 [upgradable from: 31.2.3]
ubuntu-release-upgrader-core/noble-updates 1:24.04.19 all [upgradable from: 1:24.04.16]
ubuntu-release-upgrader-gtk/noble-updates 1:24.04.19 all [upgradable from: 1:24.04.16]
udev/noble-updates 255.4-1ubuntu8.2 amd64 [upgradable from: 255.4-1ubuntu8]
vim-common/noble-updates 2:9.1.0016-1ubuntu7.1 all [upgradable from: 2:9.1.0016-1ubuntu7]
vim-tiny/noble-updates 2:9.1.0016-1ubuntu7.1 amd64 [upgradable from: 2:9.1.0016-1ubuntu7]
xdg-desktop-portal-gnome/noble-updates 46.2-0ubuntu1 amd64 [upgradable from: 46.0-1build1]
xdg-desktop-portal/noble-updates 1.18.4-1ubuntu2 amd64 [upgradable from: 1.18.3-1ubuntu1]
xkb-data/noble-updates 2.41-2ubuntu1.1 all [upgradable from: 2.41-2ubuntu1]
xxd/noble-updates 2:9.1.0016-1ubuntu7.1 amd64 [upgradable from: 2:9.1.0016-1ubuntu7]
```

pkcon update:

```
Getting updates                         [=========================]         
Finished                                [=========================]         
Loading cache                           [=========================]         
Testing changes                         [=========================]         
Finished                                [                         ] (0%)  
The following packages have to be updated:
 apparmor-4.0.1really4.0.0-beta3-0ubuntu0.1.amd64    Userspace-Analyseprogramm für AppArmor
 apport-2.28.1-0ubuntu3.all    Automatisches Erstellen von Absturzberichten zur Fehlersuche
 apport-core-dump-handler-2.28.1-0ubuntu3.all    Kernel core dump handler for Apport
 apport-gtk-2.28.1-0ubuntu3.all    GTK+ Frontend für das apport Absturzberichtssystem
 cloud-init-24.1.3-0ubuntu3.3.all    Initialisierungs- und Anpassungswerkzeug für Cloud-Instanzen
 dhcpcd-base-1:10.0.6-1ubuntu3.1.amd64    DHCPv4 and DHCPv6 dual-stack client (binaries and exit hooks)
 dracut-install-060+5-1ubuntu3.2.amd64    dracut is an event driven initramfs infrastructure (dracut-install)
 evolution-data-server-3.52.3-0ubuntu1.amd64    Evolution Datenbank-Backend-Server
 evolution-data-server-common-3.52.3-0ubuntu1.all    Datenbank-Backend-Server für Evolution (architekturunabhängige Dateien)
 gir1.2-javascriptcoregtk-4.1-2.44.2-0ubuntu0.24.04.2.amd64    Bibliothek der JavaScript-Engine von WebKitGTK - GObject-Introspektionsdaten
 gir1.2-javascriptcoregtk-6.0-2.44.2-0ubuntu0.24.04.2.amd64    Bibliothek der JavaScript-Engine von WebKitGTK - GObject-Introspektionsdaten
 gir1.2-mutter-14-46.2-1ubuntu0.24.04.1.amd64    GObject-Introspektionsdaten für den Fenstermanager Mutter
 gir1.2-webkit-6.0-2.44.2-0ubuntu0.24.04.2.amd64    Web content engine library for GTK - GObject introspection data
 gir1.2-webkit2-4.1-2.44.2-0ubuntu0.24.04.2.amd64    Web content engine library for GTK - GObject introspection data
 gnome-calculator-1:46.1-1ubuntu1~24.04.1.amd64    Taschenrechner für die GNOME-Arbeitsfläche
 gnome-shell-46.0-0ubuntu6~24.04.1.amd64    Grafische Shell für den GNOME-Desktop
 gnome-shell-common-46.0-0ubuntu6~24.04.1.all    Gemeinsame Dateien für die grafische Shell von GNOME
 gnome-shell-extension-appindicator-58-1.all    AppIndicator, KStatusNotifierItem and tray support for GNOME Shell
 gnome-shell-extension-ubuntu-tiling-assistant-46-1ubuntu1.1.all    extension which adds a Windows-like snap assist to GNOME Shell
 gnome-text-editor-46.3-0ubuntu1.amd64    simple text editor for GNOME
 gstreamer1.0-pipewire-1.0.5-1ubuntu1.amd64    Multimedia-Server PipeWire - GStreamer-1.0-Plugin
 initramfs-tools-0.142ubuntu25.1.all    Generische, modulare Erstellung eines »initramfs« (Automatisierung)
 initramfs-tools-bin-0.142ubuntu25.1.amd64    Werkzeuge zur Ausführung innerhalb von »initramfs«-Abbildern (wird von initramfs-tools verwendet)
 initramfs-tools-core-0.142ubuntu25.1.all    Generische, modulare Erstellung eines »initramfs« (wichtigste Werkzeuge)
 libapparmor1-4.0.1really4.0.0-beta3-0ubuntu0.1.amd64    AppArmor - »Change Hat«-Bibliothek
 libcamel-1.2-64t64-3.52.3-0ubuntu1.amd64    Bibliothek zur Handhabung von MIME-Nachrichten für Evolution
 libebackend-1.2-11t64-3.52.3-0ubuntu1.amd64    Werkzeugbibliothek für die Evolution-Daten-Server
 libebook-1.2-21t64-3.52.3-0ubuntu1.amd64    Client library for evolution address books
 libebook-contacts-1.2-4t64-3.52.3-0ubuntu1.amd64    Client library for evolution contacts books
 libecal-2.0-3-3.52.3-0ubuntu1.amd64    Client-Bibliothek für Evolution Calendar
 libedata-book-1.2-27t64-3.52.3-0ubuntu1.amd64    Backend-Bibliothek für Evolution-Adressbücher
 libedata-cal-2.0-2t64-3.52.3-0ubuntu1.amd64    Backend library for evolution calendars
 libedataserver-1.2-27t64-3.52.3-0ubuntu1.amd64    Werkzeugbibliothek für die Evolution-Daten-Server
 libedataserverui-1.2-4t64-3.52.3-0ubuntu1.amd64    Werkzeugbibliothek für die Evolution-Daten-Server
 libfprint-2-2-1:1.94.7+tod1-0ubuntu5~24.04.1.amd64    Asynchrone Fingerabdruckbibliothek des Projekts fprint, Laufzeitbibliotheken
 libfprint-2-tod1-1:1.94.7+tod1-0ubuntu5~24.04.1.amd64    async fingerprint library of fprint project, drivers shared libraries
 libjavascriptcoregtk-4.1-0-2.44.2-0ubuntu0.24.04.2.amd64    JavaScript engine library from WebKitGTK
 libjavascriptcoregtk-6.0-1-2.44.2-0ubuntu0.24.04.2.amd64    JavaScript engine library from WebKitGTK
 libmutter-14-0-46.2-1ubuntu0.24.04.1.amd64    window manager library from the Mutter window manager
 libnautilus-extension4-1:46.2-0ubuntu0.2.amd64    Bibliotheken für Nautilus-Komponenten - Laufzeitversion
 libnss-systemd-255.4-1ubuntu8.2.amd64    NSS-Modul mit dynamischer Auflösung von Benutzer- und Gruppennamen
 libpam-modules-1.5.3-5ubuntu5.1.amd64    Pluggable Authentication Modules für PAM
 libpam-modules-bin-1.5.3-5ubuntu5.1.amd64    Pluggable Authentication Modules für PAM - Hilfsprogramme
 libpam-runtime-1.5.3-5ubuntu5.1.all    Laufzeitunterstützung für die PAM-Bibliothek
 libpam-systemd-255.4-1ubuntu8.2.amd64    System- und Diensteverwaltung - PAM-Modul
 libpam0g-1.5.3-5ubuntu5.1.amd64    Bibliothek für Pluggable Authentication Modules
 libpipewire-0.3-0t64-1.0.5-1ubuntu1.amd64    libraries for the PipeWire multimedia server
 libpipewire-0.3-common-1.0.5-1ubuntu1.all    libraries for the PipeWire multimedia server - common files
 libpipewire-0.3-modules-1.0.5-1ubuntu1.amd64    libraries for the PipeWire multimedia server - modules
 libspa-0.2-bluetooth-1.0.5-1ubuntu1.amd64    libraries for the PipeWire multimedia server - bluetooth plugins
 libspa-0.2-modules-1.0.5-1ubuntu1.amd64    libraries for the PipeWire multimedia server Simple Plugin API - modules
 libsystemd-shared-255.4-1ubuntu8.2.amd64    System- und Diensteverwaltung - interne Laufzeitbibliothek
 libsystemd0-255.4-1ubuntu8.2.amd64    Hilfsbibliothek für systemd
 libudev1-255.4-1ubuntu8.2.amd64    Laufzeitbibliothek libudev
 libwebkit2gtk-4.1-0-2.44.2-0ubuntu0.24.04.2.amd64    Web content engine library for GTK
 libwebkitgtk-6.0-4-2.44.2-0ubuntu0.24.04.2.amd64    Web content engine library for GTK
 mutter-common-46.2-1ubuntu0.24.04.1.all    Gemeinsam genutzte Dateien für den Fenstermanager Mutter
 mutter-common-bin-46.2-1ubuntu0.24.04.1.amd64    shared programs for the Mutter window manager
 nautilus-1:46.2-0ubuntu0.2.amd64    Dateimananger und grafische Benutzeroberfläche für GNOME
 nautilus-data-1:46.2-0ubuntu0.2.all    data files for nautilus
 pipewire-1.0.5-1ubuntu1.amd64    audio and video processing engine multimedia server
 pipewire-alsa-1.0.5-1ubuntu1.amd64    PipeWire ALSA plugin, for ALSA applications to output via PipeWire
 pipewire-audio-1.0.5-1ubuntu1.all    recommended set of PipeWire packages for a standard audio desktop use
 pipewire-bin-1.0.5-1ubuntu1.amd64    PipeWire multimedia server - programs
 pipewire-pulse-1.0.5-1ubuntu1.amd64    PipeWire PulseAudio daemon
 python3-apport-2.28.1-0ubuntu3.all    Python 3 library for Apport crash report handling
 python3-distupgrade-1:24.04.19.all    Aktualisierungsverwaltung und Distributionsaktualisierung (Kernbestandteile)
 python3-problem-report-2.28.1-0ubuntu3.all    Python 3 library to handle problem reports
 systemd-255.4-1ubuntu8.2.amd64    System- und Diensteverwaltung
 systemd-dev-255.4-1ubuntu8.2.all    systemd development files
 systemd-oomd-255.4-1ubuntu8.2.amd64    userspace out-of-memory (OOM) killer
 systemd-resolved-255.4-1ubuntu8.2.amd64    systemd DNS resolver
 systemd-sysv-255.4-1ubuntu8.2.amd64    System- und Diensteverwaltung - Kompatibilitäts-Links für SysV
 systemd-timesyncd-255.4-1ubuntu8.2.amd64    Minimalistischer Dienst zur Synchronisierung der Ortszeit mit NTP-Servern
 tzdata-2024a-3ubuntu1.1.all    Zeitzonen- und Sommerzeit-Daten
 ubuntu-pro-client-32.3.1~24.04.amd64    Management tools for Ubuntu Pro
 ubuntu-pro-client-l10n-32.3.1~24.04.amd64    Translations for Ubuntu Pro Client
 ubuntu-release-upgrader-core-1:24.04.19.all    Aktualisierungsverwaltung und Distributionsaktualisierung (Kernbestandteile)
 ubuntu-release-upgrader-gtk-1:24.04.19.all    Aktualisierungsverwaltung und Distributionsaktualisierung (Kernbestandteile)
 udev-255.4-1ubuntu8.2.amd64    /dev/- und hotplug-Verwaltungsdaemon
 vim-common-2:9.1.0016-1ubuntu7.1.all    Vi IMproved &#8211; Gemeinsame Dateien
 vim-tiny-2:9.1.0016-1ubuntu7.1.amd64    Vi IMproved &#8211; Erweiterte vi-Textbearbeitung &#8211; Kompakte Version
 xdg-desktop-portal-1.18.4-1ubuntu2.amd64    Portal zur Desktop-Integration für Flatpak und Snap
 xdg-desktop-portal-gnome-46.2-0ubuntu1.amd64    GNOME-Portal-Backend für xdg-desktop-portal
 xkb-data-2.41-2ubuntu1.1.all    Konfigurationsdateien für die X Keyboard Extension (XKB)
 xxd-2:9.1.0016-1ubuntu7.1.amd64    Werkzeug zur Erzeugung (oder Umkehrung) eines Hex-Dumps
Proceed with changes? [N/y] 
```

---

### Post by #&amp;thj^% on 2024-08-04
I would definitely take those updates soon if not now.

As far as Gnome-Software goes I'm clueless as to why they are not seen and they should be.
I'm not one that rely's on GUI's for taking care of my system or keeping it current, I have a saying That if I live by any GUI I'll Die by a GUI...

I run Ubuntu,  Arch,  Debian, and Arch/Based systems and use [Topgrade]("https://www.makeuseof.com/update-everything-on-linux-with-topgrade/") to update all my packages, >Debs Flatpaks, or even snaps.
One Command that's all.

Please see this: [https://itsfoss.com/ubuntu-gnome-software-center/](https://itsfoss.com/ubuntu-gnome-software-center/)

---

