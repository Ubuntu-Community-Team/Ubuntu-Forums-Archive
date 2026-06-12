---
title: "Software center not working"
date: 2016-12-15
forum: General Help
---

### Post by tashimee2 on 2016-12-15
I installed xubuntu 16.04 on my laptop (Lenovo T60). The software center stopped working after a week. I tried running it in the terminal and got these errors:


(gnome-software:4735): Gs-WARNING **: failed to open plugin /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: cannot open shared object file: No such file or directory  (gnome-software:4735): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
(gnome-software:4735): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
(gnome-software:4735): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
(gnome-software:4735): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
(gnome-software:4735): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
(gnome-software:4735): GsPlugin-WARNING **: failed to load cached icon 64x64: Image file '/var/lib/app-info/icons/ubuntu-xenial-security-universe/64x64' contains no data
(gnome-software:4735): GLib-CRITICAL **: g_dir_read_name: assertion 'dir != NULL' failed
(gnome-software:4735): Gtk-WARNING **: Error loading image 'file:///usr/share/gnome-software/featured-polari.svg': Error opening file: Too many open files
(gnome-software:4735): GLib-ERROR **: Creating pipes for GWakeup: Too many open files
  

So I tried installing ubuntu-software and I got these errors:

                        (ubuntu-software:3013): Gs-WARNING **: failed to open plugin /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: /usr/lib/gs-plugins-9/libgs_plugin_xdg_app_reviews.so: cannot open shared object file: No such file or directory
 (ubuntu-software:3013): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
(ubuntu-software:3013): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
(ubuntu-software:3013): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
(ubuntu-software:3013): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
(ubuntu-software:3013): Gs-WARNING **: Failed to create permission org.freedesktop.packagekit.trigger-offline-update: GDBus.Errorrg.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64: Image file '/var/lib/app-info/icons/ubuntu-xenial-security-universe/64x64' contains no data
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/dosbox_dosbox.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/dosbox_dosbox.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/teeworlds_teeworlds.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/teeworlds_teeworlds.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/firefox_firefox.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/firefox_firefox.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/chromium-browser_chromium-browser.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/chromium-browser_chromium-browser.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/cairo-dock-core_cairo-dock.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/cairo-dock-core_cairo-dock.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/warzone2100_warzone2100.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/warzone2100_warzone2100.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/mypaint_mypaint.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/mypaint_mypaint.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/gelemental_gelemental.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/gelemental_gelemental.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/hugin_hugin.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/hugin_hugin.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/supertuxkart_supertuxkart.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/supertuxkart_supertuxkart.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/synapse_synapse.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/synapse_synapse.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/easystroke_easystroke.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/easystroke_easystroke.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/terminator_terminator.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/terminator_terminator.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/classicmenu-indicator_classicmenu-indicator-light.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/classicmenu-indicator_classicmenu-indicator-light.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/gnome-terminal_utilities-terminal.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/gnome-terminal_utilities-terminal.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/meld_meld.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/meld_meld.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/blender_blender.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/blender_blender.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/k3b_k3b.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/k3b_k3b.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/shutter_shutter.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/shutter_shutter.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/qbittorrent_qbittorrent.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/qbittorrent_qbittorrent.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/geogebra_geogebra.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/geogebra_geogebra.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/audacious_audacious.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/audacious_audacious.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/audacity_audacity.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/audacity_audacity.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/gimp_gimp.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/gimp_gimp.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/guake_guake.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/guake_guake.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/speedcrunch_speedcrunch.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/speedcrunch_speedcrunch.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/smplayer_smplayer.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/smplayer_smplayer.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/inkscape_inkscape.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/inkscape_inkscape.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/clementine_clementine.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/clementine_clementine.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/filezilla_filezilla.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/filezilla_filezilla.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/synaptic_synaptic.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/synaptic_synaptic.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/stellarium_stellarium.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/stellarium_stellarium.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/geany_geany.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/geany_geany.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/vlc_vlc.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/vlc_vlc.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/gparted_gparted.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/gparted_gparted.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/lyx_lyx.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/lyx_lyx.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/libreoffice-writer_libreoffice-writer.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/libreoffice-writer_libreoffice-writer.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/libreoffice-impress_libreoffice-impress.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/libreoffice-impress_libreoffice-impress.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/libreoffice-calc_libreoffice-calc.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-main/64x64/libreoffice-calc_libreoffice-calc.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/evolution_evolution.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/evolution_evolution.png': Too many open files
(ubuntu-software:3013): GsPlugin-WARNING **: failed to load cached icon 64x64/abiword_abiword.png: Failed to open file '/var/lib/app-info/icons/ubuntu-xenial-universe/64x64/abiword_abiword.png': Too many open files
(ubuntu-software:3013): GLib-CRITICAL **: g_dir_read_name: assertion 'dir != NULL' failed
(ubuntu-software:3013): Gs-WARNING **: hiding recommended applications: found only 2 to show, need at least 8
(ubuntu-software:3013): Gtk-WARNING **: Error loading image 'file:///usr/share/gnome-software/featured-polari.svg': Error opening file: Too many open files
(ubuntu-software:3013): GLib-ERROR **: Creating pipes for GWakeup: Too many open files
Trace/breakpoint trap (core dumped)

  

Please help, I'm new to linux, please try to make it easy for me.

---

