---
title: "kino"
date: 2006-11-27
forum: General Help
---

### Post by Roasted on 2006-11-27
I just installed kino. Here's everything that was displayed in the terminal. I just wanted to post and see what you folks thought of the errors I got. It opens when I launch it, but I figured I'd ask anyway.





jason@jason:~$ sudo apt-get install kino
Password:
Reading package lists... Done
Building dependency tree... Done
kino is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jason@jason:~$ sudo apt-get install kinoplus
Reading package lists... Done
Building dependency tree... Done
kinoplus is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jason@jason:~$ sudo apt-get install kino-timfx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kino-timfx: Depends: kino (>= 0.7) but it is not going to be installed
E: Broken packages
jason@jason:~$ sudo apt-get install kino-dvtitler
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kino-dvtitler: Depends: kino (>= 0.7) but it is not going to be installed
E: Broken packages
jason@jason:~$ kino
> Kino Common being built
> Creating page editor
> Creating Capture Page
> Creating Export Page
> Creating Export1394 Page
> Creating ExportAVI Page
> Creating ExportStills Page
> Creating ExportAudio Page
> Creating Preferences
Loading preferences from "/home/jason/.gnome2/kino"
Saving preferences.
> Creating ExportMJPEG Page
> Initializing MJPEG Export Page settings from Preferences
> Creating ExportPipe Page
/usr/share/kino/scripts/exports/extract_chapters
/usr/share/kino/scripts/exports/ffmpeg_divx.sh
/usr/share/kino/scripts/exports/ffmpeg_vcd.sh
/usr/share/kino/scripts/exports/ffmpeg_mp3.sh
/usr/share/kino/scripts/exports/rawplay.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd.sh
/usr/share/kino/scripts/exports/ffmpeg2theora.sh
/usr/share/kino/scripts/exports/mencoder.sh
/usr/share/kino/scripts/exports/ffmpeg_dvd_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_flv.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4.sh
/usr/share/kino/scripts/exports/ffmpeg_3gp.sh
/usr/share/kino/scripts/exports/ffmpeg_divx_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_mp4_dual.sh
/usr/share/kino/scripts/exports/ffmpeg_h264.sh
/usr/share/kino/scripts/exports/ffmpeg_h264_dual.sh
> Creating page trim
>> image creator repository created
>>> Image Create: Fixed Colour
>>> Image Create: Random noise
>>> Image Create: Colour Range
>>> Image Create: Gradiant
>>> Image Create: Create From File
>> image filter repository created
>>> Image Filter: No Change
>>> Image Filter: Black & White
>>> Image Filter: Sepia
>>> Image Filter: Reverse Video
>>> Image Filter: Mirror
>>> Image Filter: Kaleidoscope
>>> Image Filter: Swap
>> image transition repository created
>>> Image Transition: No Change
>>> Image Transition: Switch
>>> Image Transition: Fade
>>> Image Transition: Push Wipe
>>> Image Transition: Barn Door Wipe
>>> Image Transition: Differences
>> audio filter repository created
>>> Audio Filter: No Change
>>> Audio Filter: Silence
>>> Audio Filter: Fade In
>>> Audio Filter: Fade Out
>> audio transition repository created
>>> Audio Transition: No Change
>>> Audio Transition: Cross Fade
>>> Audio Transition: Dub
>>> Audio Transition: Mix
> Creating Magick Page
>> Searching /usr/lib/kino-gtk2 for plugins
>>> Registering plugin /usr/lib/kino-gtk2/libtimfx.so
>>> Registering plugin /usr/lib/kino-gtk2/libdvtitler.so
>>> Registering plugin /usr/lib/kino-gtk2/libkinoplus.so
>>> Image Filter: Blur
>>> Image Filter: Color Hold
>>> Image Filter: Soft Focus
>>> Image Transition: Luma Wipe
>>> Image Filter: Titler
>>> Image Filter: Superimpose

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed>>> Image Create: FFMPEG Import

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed
>>> Image Create: Multiple Image Import
>>> Image Filter: Jerk

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed>>> Image Filter: ImageMagick Titler

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed>>> Image Filter: ImageMagick Overlay
>>> Image Filter: Pixelate
>>> Image Filter: Charcoal
>>> Image Filter: Pan and Zoom
>>> Image Filter: Colour Average
>>> Image Filter: Gamma
>>> Image Filter: Effect TV
>>> Image Filter: Pipe Filter
>>> Image Transition: Chroma key on blue

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed
(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): GLib-CRITICAL **: g_string_prepend: assertion `val != NULL' failed>>> Image Transition: Tweenies

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed
>>> Audio Filter: FFMPEG Dub
>> Starting Editor
>> Kino Common newFile
>> Creating undo/redo buffer
>>> Received playlist to store at position 0
>>>> Adding to end
>> on_main_window_map_event
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
Exiting Kino
Saving preferences.

(kino:19889): Gnome-CRITICAL **: gnome_program_get_app_id: assertion `program != NULL' failed
jason@jason:~$
jason@jason:~$


edit - Now that I think about it I think I already had kino installed. Doh! Would that be why I got those errors?

---

### Post by reclusivemonkey on 2006-11-28
I would use apt-get to remove kino, delete your ~/.kino folder and then try again. I have installed kino through automatix and don't have any problems. It also seems to be able to import various file formats which didn't work in dapper (I upgraded to edgy).

---

