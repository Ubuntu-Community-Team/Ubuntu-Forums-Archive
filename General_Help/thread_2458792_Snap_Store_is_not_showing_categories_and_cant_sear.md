---
title: "Snap Store is not showing categories and cant search manually"
date: 2021-03-04
forum: General Help
---

### Post by cookiecrust on 2021-03-04
Hello guys,

I've been encountering this problem of my snap-store not showing choices of application as it should. Only sometimes when i open it, it works normally but now it rarely happen. I've attached the images below for reference


[ATTACH=CONFIG]288050[/ATTACH]

After that i use snap-store --quit, output is below :

```
10:42:50:0359 Gtk Failed to load module "canberra-gtk-module"
10:42:50:0361 Gtk Failed to load module "canberra-gtk-module"
10:42:50:0405 Gs  enabled plugins: desktop-categories, fwupd, os-release, packagekit, packagekit-local, packagekit-offline, packagekit-proxy, packagekit-refine-repos, packagekit-refresh, packagekit-upgrade, packagekit-url-to-app, appstream, desktop-menu-path, hardcoded-blocklist, hardcoded-popular, modalias, odrs, packagekit-refine, rewrite-resource, packagekit-history, provenance, snap, systemd-updates, generic-updates, provenance-license, icons, key-colors, key-colors-metadata
10:42:50:0405 Gs  disabled plugins: dpkg, dummy, fedora-langpacks, fedora-pkgdb-collections, repos
10:42:50:0506 Gs  /etc/PackageKit/Vendor.conf file not found
```

Then i reopen snap-store, output is below :

```
10:42:56:0613 Gtk Failed to load module "canberra-gtk-module"
10:42:56:0614 Gtk Failed to load module "canberra-gtk-module"
10:42:56:0656 Gs  enabled plugins: desktop-categories, fwupd, os-release, packagekit, packagekit-local, packagekit-offline, packagekit-proxy, packagekit-refine-repos, packagekit-refresh, packagekit-upgrade, packagekit-url-to-app, appstream, desktop-menu-path, hardcoded-blocklist, hardcoded-popular, modalias, odrs, packagekit-refine, rewrite-resource, packagekit-history, provenance, snap, systemd-updates, generic-updates, provenance-license, icons, key-colors, key-colors-metadata
10:42:56:0656 Gs  disabled plugins: dpkg, dummy, fedora-langpacks, fedora-pkgdb-collections, repos
10:42:56:0747 Gs  /etc/PackageKit/Vendor.conf file not found
10:42:58:0571 Gs  Only 0 apps for recent list, hiding
10:42:58:0572 Gs  adding wildcard app */*/*/*/org.gnome.Builder.desktop/* to plugin cache
10:42:58:0572 Gs  adding wildcard app */*/*/*/org.gnome.Calculator.desktop/* to plugin cache
10:42:58:0572 Gs  adding wildcard app */*/*/*/org.gnome.clocks.desktop/* to plugin cache
10:42:58:0572 Gs  adding wildcard app */*/*/*/org.gnome.Dictionary.desktop/* to plugin cache
10:42:58:0572 Gs  adding wildcard app */*/*/*/org.gnome.Documents.desktop/* to plugin cache
10:42:58:0573 Gs  adding wildcard app */*/*/*/org.gnome.Evince/* to plugin cache
10:42:58:0573 Gs  adding wildcard app */*/*/*/org.gnome.gedit.desktop/* to plugin cache
10:42:58:0573 Gs  adding wildcard app */*/*/*/org.gnome.Maps.desktop/* to plugin cache
10:42:58:0573 Gs  adding wildcard app */*/*/*/org.gnome.Weather/* to plugin cache
10:43:38:0591 Gs  not handling error failed for action get-featured: Get [https://api.snapcraft.io/v2/snaps/find?architecture=amd64&category=featured&confinement=strict%2Cclassic&fields=base%2Cconfinement%2Ccontact%2Cdescription%2Cdownload%2Clicense%2Cprices%2Cprivate%2Cpublisher%2Crevision%2Csummary%2Ctitle%2Ctype%2Cversion%2Cwebsite%2Cstore-url%2Cmedia%2Ccommon-ids%2Cchannel:](https://api.snapcraft.io/v2/snaps/find?architecture=amd64&category=featured&confinement=strict%2Cclassic&fields=base%2Cconfinement%2Ccontact%2Cdescription%2Cdownload%2Clicense%2Cprices%2Cprivate%2Cpublisher%2Crevision%2Csummary%2Ctitle%2Ctype%2Cversion%2Cwebsite%2Cstore-url%2Cmedia%2Ccommon-ids%2Cchannel:) net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers)
10:43:38:0593 Gs  not handling error failed for action get-category-apps: Get [https://api.snapcraft.io/v2/snaps/find?architecture=amd64&category=games-featured&confinement=strict%2Cclassic&fields=base%2Cconfinement%2Ccontact%2Cdescription%2Cdownload%2Clicense%2Cprices%2Cprivate%2Cpublisher%2Crevision%2Csummary%2Ctitle%2Ctype%2Cversion%2Cwebsite%2Cstore-url%2Cmedia%2Ccommon-ids%2Cchannel:](https://api.snapcraft.io/v2/snaps/find?architecture=amd64&category=games-featured&confinement=strict%2Cclassic&fields=base%2Cconfinement%2Ccontact%2Cdescription%2Cdownload%2Clicense%2Cprices%2Cprivate%2Cpublisher%2Crevision%2Csummary%2Ctitle%2Ctype%2Cversion%2Cwebsite%2Cstore-url%2Cmedia%2Ccommon-ids%2Cchannel:) net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers)
10:43:38:0593 Gs  hiding category games featured applications: found only 0 to show, need at least 9
10:43:38:0594 Gs  not GsPlugin error snapd-error-quark:10: status-code=500 kind=(null) message=Get [https://api.snapcraft.io/api/v1/snaps/sections:](https://api.snapcraft.io/api/v1/snaps/sections:) net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers)
10:43:38:0597 Gs  not handling error failed for action get-category-apps: Get [https://api.snapcraft.io/v2/snaps/find?architecture=amd64&category=graphics-featured&confinement=strict%2Cclassic&fields=base%2Cconfinement%2Ccontact%2Cdescription%2Cdownload%2Clicense%2Cprices%2Cprivate%2Cpublisher%2Crevision%2Csummary%2Ctitle%2Ctype%2Cversion%2Cwebsite%2Cstore-url%2Cmedia%2Ccommon-ids%2Cchannel:](https://api.snapcraft.io/v2/snaps/find?architecture=amd64&category=graphics-featured&confinement=strict%2Cclassic&fields=base%2Cconfinement%2Ccontact%2Cdescription%2Cdownload%2Clicense%2Cprices%2Cprivate%2Cpublisher%2Crevision%2Csummary%2Ctitle%2Ctype%2Cversion%2Cwebsite%2Cstore-url%2Cmedia%2Ccommon-ids%2Cchannel:) net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers)
10:43:38:0597 Gs  failed to get categories: no categories to show
10:43:38:0597 Gs  hiding category graphics featured applications: found only 0 to show, need at least 9
10:43:48:0703 Gs  not handling error download-failed for action refine: failed to download [http://people.gnome.org/~jimmac/gnome-software/steam-logo.svg:](http://people.gnome.org/~jimmac/gnome-software/steam-logo.svg:) Cannot connect to destination
10:43:48:0704 Gs  failed to get featured apps: no apps to show
10:43:48:0704 Gs  FIXME: Unknown progress handling is not yet implemented for GsProgressButton
10:43:48:0704 Gs  FIXME: Unknown progress handling is not yet implemented for GsProgressButton
10:43:48:0705 Gs  FIXME: Unknown progress handling is not yet implemented for GsProgressButton
10:43:48:0705 Gs  FIXME: Unknown progress handling is not yet implemented for GsProgressButton
10:43:48:0832 Gs  automatically prevented from changing kind on system/package/*/generic/org.a11y.brltty/* from generic to unknown!
10:44:06:0901 Gs  automatically prevented from changing kind on system/snap/*/runtime/io.snapcraft.core20-DLqre5XGLbDqg9jPtiAhRRjDuPVa5X1q/latest/stable from runtime to unknown!
10:44:07:0713 Gs  automatically prevented from changing kind on system/snap/*/desktop/io.snapcraft.snapd-PMrrV4ml8uWuEUDBT8dSGnKUYbevVhc4/latest/stable from desktop to unknown!
10:44:13:0121 Gs  automatically prevented from changing kind on system/snap/*/runtime/io.snapcraft.core18-CSO04Jhav2yK0uz97cr0ipQRyqg0qQL6/latest/stable from runtime to unknown!
```

Is there anything i can do to solve this issue? Any help would be useful :)

btw, im new to this environment & im from Malaysia :KS
Thanks in advance!

[ Ubuntu 20.04 ]

---

### Post by fsrp on 2021-11-09
Same problem here, but i can search for packages, it just doesn't show the categories, but after i did snap-store --quit and clicked again on snapstore icon everything turned out fine.
.

---

