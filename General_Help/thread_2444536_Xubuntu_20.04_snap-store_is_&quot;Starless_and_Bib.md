---
title: "Xubuntu 20.04 snap-store is &quot;Starless and Bible Black&quot;"
date: 2020-05-31
forum: General Help
---

### Post by Adam_GUI on 2020-05-31
I have snap-store installed.  It works well enough.  
It got an update the other day... and the whole thing is leather bible black with white text.

I have installed gnome-tweak-tool and tried adjusting theme there-- no change.

How do I change the theme of snap-store to be less hard-to-look-at?

Screenshot attached.

[ATTACH=CONFIG]286058[/ATTACH]

Thanks.

---

### Post by Adam_GUI on 2020-06-02
I've done some follow up.
Here's what I've found.

[https://forum.snapcraft.io/t/how-is-it-that-snap-store-uses-some-user-themes-when-other-snaps-dont/17400]("https://forum.snapcraft.io/t/how-is-it-that-snap-store-uses-some-user-themes-when-other-snaps-dont/17400")

I have found others experiencing a black, or, even transparent theme as an error fallback.
I installed the gtk-common themes snap.  No change when changing themes through xfce or gnome-tweak tools.

For me, the snap always loads as black.
Even though other snaps, like shotcut, observe the xfce-set theme.  For me, I'm using: "Pocillo-dark-slim."

From what I see, the snap-store is supposed to fall back to "Adwata" when it can't match the system theme.  But, sometimes doesn't.

If it helps, I'm also running compiz and emerald through fusion-icon (2008 is back, baby!).

It was suggested that updating the snap-store to the beta channel would provide a fix.
[https://github.com/lassekongo83/zuki-themes/issues/160]("https://github.com/lassekongo83/zuki-themes/issues/160")
Above link, final post.

It did not.  I still get a fully black interface that makes finding the install button a weird guessing-game.

I tried to log in to my Ubuntu One account in the store to see if it unlocked any theme settings.
It does not.

I don't mind snaps or having to use the snap-store.  I just wish I could manually set a snap-store theme through the UI.

I tried forcing a theme in terminal as so:
```
GTK_THEME=Pocillo-dark-slim /snap/bin/snap-store
```
I, then, repeated the process with Adwata.  No change.

I've tried installing and setting an outside theme by installing the mojave-themes pack from the snap store and setting it with:
```
sudo snap connect snap-store:gtk-3-themes mojave-themes:gtk-3-themes
```

No Change.  No matter what I do, I get a stark black theme with stark black buttons.

I would be happy with it using Numix or high-contrast if it only meant I could better see what I'm doing.

Trying to launch snap-store from terminal yields the message:
```
Failed to load module "appmenu-gtk-module"
```

apt search tells me that both appmenu-gtk-module and appmenu-registrar are installed.

I'm at a loss as how to proceed further.  I looks like there's an integration loop that isn't catching for theme.

If anyone has further ideas or knows a better place to file a bug, just let me know.

Thanks.

---

### Post by Adam_GUI on 2020-06-04
running "snap-store" from terminal now gives me the following output:
```
snap-store
17:49:01:0204 Gtk Failed to load module "appmenu-gtk-module"
17:49:01:0315 Gtk Theme parsing error: gtk.css:1:0: Failed to import: Error opening file /var/lib/snapd/hostfs/usr/share/themes/Pocillo-dark-slim/gtk-3.22/gtk.css: Permission denied
17:49:06:0610 Gs  plugin appstream took 4.4 seconds to do setup
17:49:06:0695 Gs  enabled plugins: desktop-categories, fwupd, os-release, packagekit, packagekit-local, packagekit-offline, packagekit-proxy, packagekit-refine-repos, packagekit-refresh, packagekit-upgrade, packagekit-url-to-app, appstream, desktop-menu-path, hardcoded-blacklist, hardcoded-popular, modalias, odrs, packagekit-refine, rewrite-resource, packagekit-history, provenance, snap, systemd-updates, generic-updates, provenance-license, icons, key-colors, key-colors-metadata
17:49:06:0695 Gs  disabled plugins: dpkg, dummy, fedora-langpacks, fedora-pkgdb-collections, repos
17:49:08:0693 Gs  /etc/PackageKit/Vendor.conf file not found
17:49:09:0305 Gs  lost session service
17:49:11:0347 Gs  adding wildcard app */*/*/*/org.gnome.Builder.desktop/* to plugin cache
17:49:11:0347 Gs  adding wildcard app */*/*/*/org.gnome.Calculator.desktop/* to plugin cache
17:49:11:0347 Gs  adding wildcard app */*/*/*/org.gnome.clocks.desktop/* to plugin cache
17:49:11:0348 Gs  adding wildcard app */*/*/*/org.gnome.Dictionary.desktop/* to plugin cache
17:49:11:0348 Gs  adding wildcard app */*/*/*/org.gnome.Documents.desktop/* to plugin cache
17:49:11:0349 Gs  adding wildcard app */*/*/*/org.gnome.Evince/* to plugin cache
17:49:11:0349 Gs  adding wildcard app */*/*/*/org.gnome.gedit.desktop/* to plugin cache
17:49:11:0349 Gs  Only 0 apps for recent list, hiding
17:49:11:0350 Gs  adding wildcard app */*/*/*/org.gnome.Maps.desktop/* to plugin cache
17:49:11:0352 Gs  adding wildcard app */*/*/*/org.gnome.Weather/* to plugin cache
17:49:11:0964 Gs  hiding category graphics featured applications: found only 0 to show, need at least 9
17:49:11:0964 Gs  hiding category productivity featured applications: found only 0 to show, need at least 9
17:49:15:0267 Gs  automatically prevented from changing kind on system/package/*/generic/io.elementary.granite/* from generic to unknown!
17:49:58:0230 Gs  automatically prevented from changing kind on system/snap/*/runtime/io.snapcraft.core18-CSO04Jhav2yK0uz97cr0ipQRyqg0qQL6/latest/stable from runtime to unknown!

```

I realized I misspelled Adwaita and changed my variable to Adwaita-dark as so:
```
GTK_THEME=Adwaita-dark /snap/bin/snap-store
17:55:16:0221 Gtk Failed to load module "appmenu-gtk-module"
17:55:16:0393 Gs  enabled plugins: desktop-categories, fwupd, os-release, packagekit, packagekit-local, packagekit-offline, packagekit-proxy, packagekit-refine-repos, packagekit-refresh, packagekit-upgrade, packagekit-url-to-app, appstream, desktop-menu-path, hardcoded-blacklist, hardcoded-popular, modalias, odrs, packagekit-refine, rewrite-resource, packagekit-history, provenance, snap, systemd-updates, generic-updates, provenance-license, icons, key-colors, key-colors-metadata
17:55:16:0393 Gs  disabled plugins: dpkg, dummy, fedora-langpacks, fedora-pkgdb-collections, repos
17:55:16:0577 Gs  /etc/PackageKit/Vendor.conf file not found
17:55:16:0871 Gs  lost session service
17:55:19:0307 Gs  adding wildcard app */*/*/*/org.gnome.Builder.desktop/* to plugin cache
17:55:19:0307 Gs  adding wildcard app */*/*/*/org.gnome.Calculator.desktop/* to plugin cache
17:55:19:0307 Gs  adding wildcard app */*/*/*/org.gnome.clocks.desktop/* to plugin cache
17:55:19:0307 Gs  adding wildcard app */*/*/*/org.gnome.Dictionary.desktop/* to plugin cache
17:55:19:0307 Gs  adding wildcard app */*/*/*/org.gnome.Documents.desktop/* to plugin cache
17:55:19:0307 Gs  adding wildcard app */*/*/*/org.gnome.Evince/* to plugin cache
17:55:19:0307 Gs  adding wildcard app */*/*/*/org.gnome.gedit.desktop/* to plugin cache
17:55:19:0307 Gs  adding wildcard app */*/*/*/org.gnome.Maps.desktop/* to plugin cache
17:55:19:0307 Gs  adding wildcard app */*/*/*/org.gnome.Weather/* to plugin cache
17:55:19:0313 Gs  Only 0 apps for recent list, hiding
17:55:20:0128 Gs  hiding category productivity featured applications: found only 0 to show, need at least 9
17:55:20:0139 Gs  hiding category graphics featured applications: found only 0 to show, need at least 9
17:55:21:0651 Gs  automatically prevented from changing kind on system/package/*/generic/io.elementary.granite/* from generic to unknown!
17:55:31:0056 Gs  automatically prevented from changing kind on system/snap/*/runtime/io.snapcraft.core18-CSO04Jhav2yK0uz97cr0ipQRyqg0qQL6/latest/stable from runtime to unknown!

```

I now have an acceptable looking snap-store.

Screenshot attached:
[ATTACH=CONFIG]286092[/ATTACH]

Marking thread as solved.

---

### Post by Adam_GUI on 2020-06-08
So, Um...  Problem's back...
Thread no longer marked as solved.

[ATTACH=CONFIG]286166[/ATTACH]

"Snap-store" in terminal yields the following:
```
 snap-store
01:30:38:0930 Gtk Failed to load module "appmenu-gtk-module"

```

Apt search doesn't yield an exact package with that name.

The above work-around also no longer works
```
GTK_THEME=Adwaita-dark /snap/bin/snap-store
01:32:51:0805 Gtk Failed to load module "appmenu-gtk-module"

```

How do I get "appmenu-gtk-module"?

I just want to be able to navigate snap-store with some color-contrast.

-------------------------------------------------------------------------------
I've just run "sudo snap remove snap-store" and "sudo snap install snap-store"
The theme has defaulted to Adwaita.
I no longer have the ability to log in...  Weird.
I have color contrast again, though.  So, that's good.

Screenshot attached.
[ATTACH=CONFIG]286167[/ATTACH]

Re-reran uninstall and installed from Beta channel.
I have login and update back.  It doesn't see appmenu-gtk-module, to spite it being installed.
The theme is still matte black.  Something about the beta channel doesn't load adwaita correctly.  My google-fu isn't good enough to find a straight answer.

---

