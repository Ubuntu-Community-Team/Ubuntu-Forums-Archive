---
title: "Rsync: Permission denied migrating home folder from old to new hard drive.."
date: 2014-12-25
forum: General Help
---

### Post by killabee44 on 2014-12-25
Hi all,

I am trying to migrate a home folder from a non gpt hard drive to a new, larger gpt drive. My plan is to do a fresh install, but keep my home folder with all settings and permissions. 

The old install is giving me problems with video, but since I need to migrate to a larger drive, I figured I'd just do a fresh install anyway. This means I can't do this from within the source install. I have to do it from a live cd. 

I am trying to copy the home folder using rsync, but keep getting permission 13 errors. 

Thanks for any help you can give.

Here's the output:

```
**** default - Thu Dec 25 18:55:20 2014

** Launching RSYNC command:
rsync -r -t -p -o -g -v --progress -l -s /media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c /media/mythbuntu/_home

sending incremental file list
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.adobe" failed: Permission denied (13)
2dfd438b-957d-403c-99c7-95fd6b44726c/
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/chromium" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/compizconfig-1" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/dconf" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/evolution" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/gegl-0.2" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/mozilla" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/nuvolaplayer" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/sessions" failed: Permission denied (13)
rsync: recv_generator: mkdir "/media/mythbuntu/_home/2dfd438b-957d-403c-99c7-95fd6b44726c" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/software-center/software-center-agent.db" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/thumbnails" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/upstart" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/vlc" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/wallpaper" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.cache/webkit" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/Thunar" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/chromium" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/compiz-1" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/enchant" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/evolution" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/gtk-2.0" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/htop" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/ibus" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/menus" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/pulse" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/totem" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/update-notifier" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/upstart" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/vlc" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xarchiver" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4-session" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/desktop" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/panel/launcher-11" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/panel/launcher-12" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/panel/launcher-13" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/panel/launcher-6" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/panel/launcher-7" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/panel/launcher-8" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/panel/launcher-9" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/terminal" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/xfconf/xfce-perchannel-xml" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.config/xfce4/xfwm4" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.dbus" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.dropbox" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.gconf" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.gnome" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.gnome2" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.gnome2_private" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.grsync" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.gvfs" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.local/share" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.macromedia" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.mozilla" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.nv" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.pki" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.sabnzbd/admin/future" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/.thumbnails" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/Dropbox" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/logs/refs/remotes/origin/feature" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/01" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/02" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/06" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/07" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/08" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/09" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/0c" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/0e" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/0f" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/10" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/11" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/12" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/13" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/14" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/15" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/17" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/19" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/1a" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/1d" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/1e" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/1f" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/22" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/23" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/25" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/26" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/27" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/28" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/2b" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/2d" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/2e" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/2f" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/30" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/32" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/33" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/34" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/35" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/36" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/38" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/3a" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/3b" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/3c" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/3d" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/3e" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/3f" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/40" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/41" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/43" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/44" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/47" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/49" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/4a" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/4b" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/4d" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/4e" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/4f" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/51" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/54" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/56" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/57" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/58" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/5b" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/5d" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/5f" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/61" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/62" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/63" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/65" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/66" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/68" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/69" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/6a" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/6d" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/6e" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/6f" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/70" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/71" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/72" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/73" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/74" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/77" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/78" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/79" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/7b" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/7d" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/7e" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/7f" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/81" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/84" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/85" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/86" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/87" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/88" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/8a" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/8c" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/8d" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/8e" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/90" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/92" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/93" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/94" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/95" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/97" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/98" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/99" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/9c" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/9e" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/9f" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/a0" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/a1" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/a2" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/a3" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/a5" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/a6" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/a8" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/a9" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/aa" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ac" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ae" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/af" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/b3" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/b4" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/b7" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/b8" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ba" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/bb" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/be" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/bf" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/c0" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/c1" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/c2" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/c4" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/c5" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/c6" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/c7" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ca" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/cc" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/cd" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ce" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/cf" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/d0" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/d1" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/d2" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/d3" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/d5" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/d6" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/d8" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/da" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/db" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/dc" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/dd" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/df" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/e0" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/e1" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/e2" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/e3" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/e8" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ea" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ec" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ed" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ee" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ef" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/f1" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/f2" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/f4" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/f6" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/f7" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/f9" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/fa" failed: Permission denied (13)

rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/fb" failed: Permission denied (13)
sent 1,653,266 bytes  received 7,790 bytes  1,107,370.67 bytes/sec
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/fd" failed: Permission denied (13)
total size is 9,765,914,501  speedup is 5,879.34
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/fe" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/ff" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/refs/remotes/origin/feature" failed: Permission denied (13)
rsync: opendir "/media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/cache/sessions" failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.0]
Rsync process exit status: 23

```

---

### Post by nerdtron on 2014-12-25
What is the permissions of the source and destination directories?
```
ls -l /media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c
ls -l /media/mythbuntu/_home
```
And let's have a sample permission on the files to be transferred
```
ls -l /media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/fb

```

---

### Post by killabee44 on 2014-12-25
> **nerdtron said:**
> What is the permissions of the source and destination directories?
```
ls -l /media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c
ls -l /media/mythbuntu/_home
```
And let's have a sample permission on the files to be transferred
```
ls -l /media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/fb

```

]ls -l /media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c:

```
drwxr-xr-x 45   1000   1000  4096 Dec 23 04:20 htpc1
drwxrwxrwx  2 root   root   16384 Dec  5  2009 lost+found
drwxr-xr-x  4 mythtv mythtv  4096 May 10  2014 mythtv
drwxr-xr-x  3 root   root    4096 May 16  2014 user

```

ls -l /media/mythbuntu/_home:

```
drwx------ 2 root root 16384 Dec 23 22:16 lost+found
mythbuntu@mythbuntu:/media/mythbuntu/_home$ 

```


ls -l /media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/fb:

```
ls: cannot open directory /media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c/htpc1/sickrage_install/.git/objects/fb: Permission denied

```

---

### Post by nerdtron on 2014-12-25
So it seems you don't have permissions to view/read the source folder.

Have you tried using rsync with sudo? like "sudo rsync "

If its successful then you can change the permission/ownership of the folders after that.
Or if you like to do it now.
```
 sudo chmod -R a+r /media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c 
```
Then try the rsync command again.

---

### Post by killabee44 on 2014-12-25
> **nerdtron said:**
> So it seems you don't have permissions to view/read the source folder.

Have you tried using rsync with sudo? like "sudo rsync "

If its successful then you can change the permission/ownership of the folders after that.
Or if you like to do it now.
```
 sudo chmod -R a+r /media/mythbuntu/2dfd438b-957d-403c-99c7-95fd6b44726c 
```
Then try the rsync command again.

Thanks. But if I change the permissions, wouldn't I have problems later on? Or would the old permissions still be implemented in the new copies? It's gonna be a new install and I really don't want to mess it up.

EDIT:

Tried it with sudo rsync and it worked. Don't know why I didn't think of that lol. Well, on to the install. Hopefully all goes well. Ill post back with results. 
Thanks.

---

### Post by nerdtron on 2014-12-25
I think if you are the owner to all the files (source and destination) you should change the permissions and ownership so that the files will be owned by your user account. They are you files after all. You just need to do this once, and you be able to copy/edit/paste/modify the files.

The sudo will just retain everything the current permission and it's just a temporary (maybe a force) workaround to the problem.

---

### Post by killabee44 on 2014-12-25
Alright, I did he install and my files are there, but in a different home folder. The name of the old home folder is really long and made up of random characters and numbers. Im not sure if it was rsync or the new install that caused this.  So, the install didn't identify it as my home folder and created another home folder with the proper name. 

How do I go about restoring the old home folder? Can I just copy and paste? Thanks.

---

### Post by nerdtron on 2014-12-25
> **killabee44 said:**
> Alright, I did he install and my files are there, but in a different home folder. 


What is the folder structure now? which files do you want to transfer, where are they and where do you want to put them?

> The name of the old home folder is really long and made up of random characters and numbers.
That long folder name with random characters and numbers is the probably the external drive that you used to backup your home folder.
> 
Im not sure if it was rsync or the new install that caused this.  So,  the install didn't identify it as my home folder and created another  home folder with the proper name. 
How do I go about restoring the old home folder? Thanks.
Hmmm now looking back on your original rsync command. It seems that your copied the backup folder 2dfd438b-957d-403c-99c7-95fd6b44726c to the /media/mythbuntu/_home.

Do you have a GUI? you can just move the files over to the folders you want.
To change ownership for the files:
```
sudo chown -R username:username /media/mythbuntu/*

```
Replace the username with your user account name.

---

### Post by killabee44 on 2014-12-25
Ok, Ill just use rsync again to copy the files over. Im using the same username on the new install and the same password as well, so I don't think Ill have to change ownerwhip, but in case I do, Ill keep that command handy. Thanks.

---

