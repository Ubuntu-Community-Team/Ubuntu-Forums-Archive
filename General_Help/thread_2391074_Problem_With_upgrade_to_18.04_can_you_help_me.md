---
title: "Problem With upgrade to 18.04 can you help me?"
date: 2018-05-05
forum: General Help
---

### Post by gedas07 on 2018-05-05
Today I try to update my Ubuntu 16.04 to 18.04 , and when the terminal finish and i reboot the system, in about the version in 16.04 
and when i try in terminal sudo apt-get update    sudo apt-get upgrade say this  can you help me? please

```
gedas07@gedas07-SERVER:~$ sudo apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... falló.
Los siguientes paquetes tienen dependencias incumplidas:
 apt-xapian-index : Depende: python3-xapian (>= 1.4.3-1) pero no está instalado
 dh-python : Depende: python3-distutils pero no está instalado
 gnome-icon-theme : Depende: gtk-update-icon-cache
 gnome-settings-daemon : Depende: libfontconfig1 (>= 2.12) pero 2.11.94-0ubuntu1.1 está instalado
                         Depende: libgeoclue-2-0 (>= 2.4.0) pero no está instalado
                         Depende: libglib2.0-0 (>= 2.53.0) pero 2.48.2-0ubuntu1 está instalado
                         Depende: libgnome-desktop-3-17 (>= 3.17.92) pero no está instalado
                         Depende: libgtk-3-0 (>= 3.21.5) pero 3.18.9-1ubuntu3.3 está instalado
                         Depende: libgweather-3-15 (>= 3.10.0) pero no está instalado
 libnautilus-extension1a : Depende: libglib2.0-0 (>= 2.51.2) pero 2.48.2-0ubuntu1 está instalado
 nautilus : Depende: libexempi3 (>= 2.4.0) pero 2.2.2-2 está instalado
            Depende: libglib2.0-0 (>= 2.51.2) pero 2.48.2-0ubuntu1 está instalado
            Depende: libgnome-autoar-0-0 (>= 0.2.1) pero no está instalado
            Depende: libgnome-desktop-3-17 (>= 3.18.1) pero no está instalado
            Depende: libgtk-3-0 (>= 3.22.6) pero 3.18.9-1ubuntu3.3 está instalado
            Depende: libtracker-sparql-2.0-0 (>= 0.10.0) pero no está instalado
            Depende: nautilus-data (= 1:3.26.3-0ubuntu4) pero 1:3.18.4.is.3.14.3-0ubuntu6 está instalado
 onboard : Depende: onboard-common (< 1.4.1-2ubuntu1.1) pero no está instalado
           Depende: onboard-common (>= 1.4.1-2ubuntu1) pero no está instalado
           Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
           Depende: libhunspell-1.6-0 pero no está instalado
           Recomienda: onboard-data (>= 1.4.1-2ubuntu1) pero 1.2.0-0ubuntu5 está instalado
 python-apt : Depende: libapt-inst2.0 (>= 1.4~beta3) pero 1.2.26 está instalado
              Depende: libapt-pkg5.0 (>= 1.4~beta3) pero 1.2.26 está instalado
 python3-apt : Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
               Depende: libapt-inst2.0 (>= 1.4~beta3) pero 1.2.26 está instalado
               Depende: libapt-pkg5.0 (>= 1.4~beta3) pero 1.2.26 está instalado
 python3-cairo : Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
 python3-gdbm : Depende: python3 (>= 3.6.4-1~) pero 3.5.1-3 está instalado
                Depende: libgdbm5 (>= 1.14) pero no está instalado
 python3-renderpm : Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
 python3-reportlab-accel : Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
 python3-smbc : Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
 rhythmbox : Depende: rhythmbox-data (= 3.3-1ubuntu7) pero 3.4.2-4ubuntu1 está instalado
             Recomienda: rhythmbox-plugins pero no está instalado
 rhythmbox-plugin-cdrecorder : Depende: librhythmbox-core10 (>= 3.0) pero no está instalado
                               Depende: rhythmbox (= 3.4.2-4ubuntu1) pero 3.3-1ubuntu7 está instalado
 rhythmbox-plugin-zeitgeist : Depende: rhythmbox (>= 3.4) pero 3.3-1ubuntu7 está instalado
 totem-plugins : Depende: libgtk-3-0 (>= 3.19.4) pero 3.18.9-1ubuntu3.3 está instalado
                 Depende: liblirc-client0 pero no está instalado
                 Depende: libtotem0 (>= 3.26.0-0ubuntu6) pero 3.18.1-1ubuntu4 está instalado
                 Depende: totem (= 3.26.0-0ubuntu6) pero 3.18.1-1ubuntu4 está instalado
                 Depende: gir1.2-totem-1.0 (= 3.26.0-0ubuntu6) pero 3.18.1-1ubuntu4 está instalado
E: Error, pkgProblemResolver::Resolve generó cortes, esto puede deberse a paquetes retenidos.
E: No se pueden corregir las dependencias
```

---

### Post by yazdzik-k on 2018-05-05
¿qué ocurre si se proba:



```
sudo apt-get dist-upgrade
sudo update-manager -d 
```


?

---

### Post by gedas07 on 2018-05-05
> **yazdzik-k said:**
> ¿qué ocurre si se proba:



```
sudo apt-get dist-upgrade
sudo update-manager -d 
```


?
```
Esto
gedas07@gedas07-SERVER:~$ sudo apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt-get -f install» para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
 apt-xapian-index : Depende: python3-xapian (>= 1.4.3-1) pero no está instalado
 dh-python : Depende: python3-distutils pero no está instalado
 gnome-icon-theme : Depende: gtk-update-icon-cache
 gnome-settings-daemon : Depende: libfontconfig1 (>= 2.12) pero 2.11.94-0ubuntu1.1 está instalado
                         Depende: libgeoclue-2-0 (>= 2.4.0) pero no está instalado
                         Depende: libglib2.0-0 (>= 2.53.0) pero 2.48.2-0ubuntu1 está instalado
                         Depende: libgnome-desktop-3-17 (>= 3.17.92) pero no está instalado
                         Depende: libgtk-3-0 (>= 3.21.5) pero 3.18.9-1ubuntu3.3 está instalado
                         Depende: libgweather-3-15 (>= 3.10.0) pero no está instalado
 libnautilus-extension1a : Depende: libglib2.0-0 (>= 2.51.2) pero 2.48.2-0ubuntu1 está instalado
 nautilus : Depende: libexempi3 (>= 2.4.0) pero 2.2.2-2 está instalado
            Depende: libglib2.0-0 (>= 2.51.2) pero 2.48.2-0ubuntu1 está instalado
            Depende: libgnome-autoar-0-0 (>= 0.2.1) pero no está instalado
            Depende: libgnome-desktop-3-17 (>= 3.18.1) pero no está instalado
            Depende: libgtk-3-0 (>= 3.22.6) pero 3.18.9-1ubuntu3.3 está instalado
            Depende: libtracker-sparql-2.0-0 (>= 0.10.0) pero no está instalado
            Depende: nautilus-data (= 1:3.26.3-0ubuntu4) pero 1:3.18.4.is.3.14.3-0ubuntu6 está instalado
 onboard : Depende: onboard-common (< 1.4.1-2ubuntu1.1) pero no está instalado
           Depende: onboard-common (>= 1.4.1-2ubuntu1) pero no está instalado
           Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
           Depende: libhunspell-1.6-0 pero no está instalado
           Recomienda: onboard-data (>= 1.4.1-2ubuntu1) pero 1.2.0-0ubuntu5 está instalado
 python-apt : Depende: libapt-inst2.0 (>= 1.4~beta3) pero 1.2.26 está instalado
              Depende: libapt-pkg5.0 (>= 1.4~beta3) pero 1.2.26 está instalado
 python3-apt : Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
               Depende: libapt-inst2.0 (>= 1.4~beta3) pero 1.2.26 está instalado
               Depende: libapt-pkg5.0 (>= 1.4~beta3) pero 1.2.26 está instalado
 python3-cairo : Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
 python3-gdbm : Depende: python3 (>= 3.6.4-1~) pero 3.5.1-3 está instalado
                Depende: libgdbm5 (>= 1.14) pero no está instalado
 python3-renderpm : Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
 python3-reportlab-accel : Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
 python3-smbc : Depende: python3 (>= 3.6~) pero 3.5.1-3 está instalado
 rhythmbox : Depende: rhythmbox-data (= 3.3-1ubuntu7) pero 3.4.2-4ubuntu1 está instalado
             Recomienda: rhythmbox-plugins pero no está instalado
 rhythmbox-plugin-cdrecorder : Depende: librhythmbox-core10 (>= 3.0) pero no está instalado
                               Depende: rhythmbox (= 3.4.2-4ubuntu1) pero 3.3-1ubuntu7 está instalado
 rhythmbox-plugin-zeitgeist : Depende: rhythmbox (>= 3.4) pero 3.3-1ubuntu7 está instalado
 totem-plugins : Depende: libgtk-3-0 (>= 3.19.4) pero 3.18.9-1ubuntu3.3 está instalado
                 Depende: liblirc-client0 pero no está instalado
                 Depende: libtotem0 (>= 3.26.0-0ubuntu6) pero 3.18.1-1ubuntu4 está instalado
                 Depende: totem (= 3.26.0-0ubuntu6) pero 3.18.1-1ubuntu4 está instalado
                 Depende: gir1.2-totem-1.0 (= 3.26.0-0ubuntu6) pero 3.18.1-1ubuntu4 está instalado
E: Dependencias incumplidas. Pruebe de nuevo utilizando -f.
gedas07@gedas07-SERVER:~$ sudo update-manager -d
/usr/bin/update-manager:28: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 38, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 36, in <module>
    import apt_pkg
ImportError: No module named 'apt_pkg'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 23, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ImportError: No module named 'apt_pkg'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 38, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdateManager.py", line 36, in <module>
    import apt_pkg
ImportError: No module named 'apt_pkg'
```

---

### Post by wildmanne39 on 2018-05-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by gedas07 on 2018-05-05
ok sorry

---

### Post by wildmanne39 on 2018-05-05
No worries!:)

---

### Post by gedas07 on 2018-05-05
well i change sources.list for one of xenial 
i do update and upgrade , another time i change source.list for one of 18.04 . i make 
apt-get dist-upgrade.
and now without errors
but when i try to start sesion ubuntu say error in the start sesion

---

