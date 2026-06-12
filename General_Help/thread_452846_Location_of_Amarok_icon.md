---
title: "Location of Amarok icon"
date: 2007-05-23
forum: General Help
---

### Post by Yggdrasill on 2007-05-23
I just need to know where the icon for Amarok is located.  I tried /usr/share/pixmaps, but there's only a 32x32 .png.  I was hoping for a larger image.

---

### Post by mlind on 2007-05-23
```

dpkg -S amarok | grep amarok.png

```

> 
amarok: /usr/share/icons/hicolor/48x48/apps/amarok.png
amarok: /usr/share/icons/hicolor/16x16/apps/amarok.png
amarok: /usr/share/icons/hicolor/128x128/apps/amarok.png
amarok: /usr/share/icons/hicolor/64x64/apps/amarok.png
amarok: /usr/share/icons/hicolor/22x22/apps/amarok.png
amarok: /usr/share/icons/hicolor/32x32/apps/amarok.png


Probably one of these?

---

### Post by Yggdrasill on 2007-05-23
Thank you very much, mlind!

---

### Post by mlind on 2007-05-23
It seems that there are 'tangofied' icons too, installed by *tango-icon-theme-common* package, but not amarok itself.

You can use slocate to search the icons more effectively
```

slocate amarok.png

```

---

### Post by fakie_flip on 2007-06-23
```
chris@ubuntu:~$ sudo find / -iname '*amarok*' -exec bash -c "file {} | grep image" \;
/usr/share/icons/hicolor/64x64/apps/amarok.png: PNG image data, 64 x 64, 8-bit/color RGBA, non-interlaced
/usr/share/icons/hicolor/48x48/apps/amarok.png: PNG image data, 48 x 48, 8-bit/color RGBA, non-interlaced
/usr/share/icons/hicolor/16x16/apps/amarok.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/icons/hicolor/32x32/apps/amarok.png: PNG image data, 32 x 32, 8-bit/color RGBA, non-interlaced
/usr/share/icons/hicolor/22x22/apps/amarok.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/icons/hicolor/128x128/apps/amarok.png: PNG image data, 128 x 128, 8-bit/color RGBA, non-interlaced
/usr/share/icons/Tango/24x24/apps/amarok.png: PNG image data, 24 x 24, 8-bit/color RGBA, non-interlaced
/usr/share/icons/Tango/16x16/apps/amarok.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/icons/Tango/22x22/apps/amarok.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/doc/kde/HTML/nl/amarok/amarok_playlist.png: PNG image data, 874 x 639, 8-bit/color RGBA, non-interlaced
/usr/share/doc/kde/HTML/it/amarok/amarok_playlist.png: PNG image data, 907 x 708, 8-bit/color RGBA, non-interlaced
/usr/share/doc/kde/HTML/sv/amarok/amarok_playlist.png: PNG image data, 855 x 619, 8-bit colormap, non-interlaced
/usr/share/doc/kde/HTML/pt/amarok/amarok_playlist.png: PNG image data, 847 x 626, 8-bit/color RGB, non-interlaced
/usr/share/doc/kde/HTML/es/amarok/amarok_playlist.png: PNG image data, 937 x 553, 8-bit/color RGBA, non-interlaced
/usr/share/doc/kde/HTML/en/amarok/amarok_playlist.png: PNG image data, 882 x 708, 8-bit/color RGBA, non-interlaced
/usr/share/doc/kde/HTML/de/amarok/amarok_playlist.png: PNG image data, 875 x 529, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/scripts/webcontrol/amarok_cut.png: PNG image data, 64 x 64, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_download.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_settings_engine.png: PNG image data, 63 x 64, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_mostplayed.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_settings_general.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_device.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_info.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_play.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_lyrics.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_repeat_no.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_rewind.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_dynamic.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_refresh.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_album.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_random_album.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_pause.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_equalizer.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_random_track.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_repeat_album.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_configure.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_artist.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_search.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_burn.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_redo.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_next.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_undo.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_random_no.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_files2.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_love.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_stop.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_external.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_save.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_covermanager.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_settings_indicator.png: PNG image data, 63 x 64, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_random.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_magnatune.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_playlist_refresh.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_edit.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_repeat_track.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_remove_from_playlist.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_fastforward.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_favourite_genres.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_podcast.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_rescan.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_circle.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_collection.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_add_playlist.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_change_language.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_track.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_scripts.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_add_lyrics.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_queue.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_music.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_repeat_playlist.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_playlist.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_clock.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_editcopy.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_remove.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_back.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_playlist_clear.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_podcast2.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_visualizations.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_audioscrobbler.png: PNG image data, 64 x 63, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_settings_playback.png: PNG image data, 64 x 64, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_files.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_settings_view.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/64x64/actions/amarok_zoom.png: PNG image data, 64 x 64, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_download.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_settings_engine.png: PNG image data, 48 x 48, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_mostplayed.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_settings_general.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_device.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_info.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_play.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_lyrics.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_repeat_no.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_rewind.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_dynamic.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_refresh.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_album.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_random_album.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_pause.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_equalizer.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_random_track.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_repeat_album.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_configure.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_artist.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_search.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_burn.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_redo.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_next.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_undo.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_random_no.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_files2.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_love.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_stop.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_external.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_save.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_covermanager.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_settings_indicator.png: PNG image data, 47 x 48, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_random.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_magnatune.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_playlist_refresh.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_edit.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_repeat_track.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_remove_from_playlist.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_fastforward.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_favourite_genres.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_podcast.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_rescan.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_circle.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_collection.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_add_playlist.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_change_language.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_track.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_scripts.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_add_lyrics.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_queue.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_music.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_repeat_playlist.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_playlist.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_clock.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_editcopy.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_remove.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_back.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_playlist_clear.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_podcast2.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_visualizations.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_audioscrobbler.png: PNG image data, 48 x 47, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_settings_playback.png: PNG image data, 48 x 48, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_files.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_settings_view.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/48x48/actions/amarok_zoom.png: PNG image data, 48 x 48, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_download.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_settings_engine.png: PNG image data, 15 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_mostplayed.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_settings_general.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_device.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_info.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_play.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_lyrics.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_repeat_no.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_rewind.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_dynamic.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_refresh.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_album.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_random_album.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_pause.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_equalizer.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_random_track.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_repeat_album.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_configure.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_artist.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_search.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_burn.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_redo.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_next.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_undo.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_random_no.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_files2.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_love.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_stop.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_external.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_save.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_covermanager.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_settings_indicator.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_random.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_magnatune.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_playlist_refresh.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_edit.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_repeat_track.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_remove_from_playlist.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_fastforward.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_favourite_genres.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_podcast.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_rescan.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_circle.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_collection.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_add_playlist.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_change_language.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_track.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_scripts.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_add_lyrics.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_queue.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_music.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_repeat_playlist.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_playlist.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_clock.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_editcopy.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_remove.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_back.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_playlist_clear.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_podcast2.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_visualizations.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_audioscrobbler.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_settings_playback.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_files.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_settings_view.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/16x16/actions/amarok_zoom.png: PNG image data, 16 x 16, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_download.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_settings_engine.png: PNG image data, 32 x 32, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_mostplayed.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_settings_general.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_device.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_info.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_play.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_lyrics.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_repeat_no.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_rewind.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_dynamic.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_refresh.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_album.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_random_album.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_pause.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_equalizer.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_random_track.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_repeat_album.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_configure.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_artist.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_search.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_burn.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_redo.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_next.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_undo.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_random_no.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_files2.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_love.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_stop.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_external.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_save.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_covermanager.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_settings_indicator.png: PNG image data, 32 x 32, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_random.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_magnatune.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_playlist_refresh.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_edit.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_repeat_track.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_remove_from_playlist.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_fastforward.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_favourite_genres.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_podcast.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_rescan.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_circle.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_collection.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_add_playlist.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_change_language.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_track.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_scripts.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_add_lyrics.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_queue.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_music.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_repeat_playlist.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_playlist.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_clock.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_editcopy.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_remove.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_back.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_playlist_clear.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_podcast2.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_visualizations.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_audioscrobbler.png: PNG image data, 32 x 32, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_settings_playback.png: PNG image data, 32 x 32, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_files.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_settings_view.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/32x32/actions/amarok_zoom.png: PNG image data, 32 x 32, 8-bit colormap, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_download.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_settings_engine.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_mostplayed.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_settings_general.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_device.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_info.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_play.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_lyrics.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_repeat_no.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_rewind.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_dynamic.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_refresh.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_album.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_random_album.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_pause.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_equalizer.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_random_track.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_repeat_album.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_configure.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_artist.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced
/usr/share/apps/amarok/icons/hicolor/22x22/actions/amarok_search.png: PNG image data, 22 x 22, 8-bit/color RGBA, non-interlaced

<snip>

/usr/share/apps/amarok/images/amarok_rocks.jpg: JPEG image data, JFIF standard 1.01
/usr/share/apps/amarok/images/amarok_cut.png: PNG image data, 64 x 64, 8-bit/color RGBA, non-interlaced
/usr/share/app-install/icons/amarok.png: PNG image data, 48 x 48, 8-bit/color RGBA, non-interlaced
/usr/share/pixmaps/amarok.xpm: X pixmap image text
/usr/share/pixmaps/amarok-16.xpm: X pixmap image text
chris@ubuntu:~$ 
```

---

