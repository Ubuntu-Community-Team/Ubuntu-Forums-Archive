---
title: "Banshee freezes/crashes since updating to 13.10"
date: 2013-10-23
forum: General Help
---

### Post by mGXbbec on 2013-10-23
I updated to ubuntu 13.10 and now when I try to launch Banshee it either freezes or closes.  Both happen within seconds of banshee starting up.  I ran banshee -debug and got this:



[Info  20:03:17.431] Running Banshee 2.6.1: [Ubuntu Saucy Salamander (development branch) (linux-gnu, x86_64) @ 2013-06-05 17:04:07 UTC]

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkComponent) to class (__gtksharp_45_Hyena_Gui_BaseWidgetAccessible) after class_init

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_46_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_46_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_TrackInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_52_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_52_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_Database_QueryFilterInfo+601+5b+5bSystem_String+2c+20mscorlib+2c+20Version+3d4_0_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3db77a5c561934e089+5d+5d+2c+20Banshee_Services+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_58_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_58_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_ArtistInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_64_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_64_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_YearInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkTable) to class (__gtksharp_70_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init

(Banshee:2250): GLib-GObject-WARNING **: attempting to add an interface (AtkSelection) to class (__gtksharp_70_Hyena_Data_Gui_Accessibility_ListViewAccessible+601+5b+5bBanshee_Collection_AlbumInfo+2c+20Banshee_Core+2c+20Version+3d2_6_0_0+2c+20Culture+3dneutral+2c+20PublicKeyToken+3dnull+5d+5d) after class_init
[Info  20:03:23.175] Updating web proxy from GConf
[Info  20:03:23.213] All services are started 4.179835
[Info  20:03:27.780] nereid Client Started
[Info  20:03:27.963] GStreamer version 1.0.7.0, gapless: True, replaygain: True
banshee: PeakFinder.cpp:150: int soundtouch::PeakFinder::findCrossingLevel(const float*, float, int, int) const: Assertion `peaklevel >= level' failed.

Native stacktrace:

    banshee() [0x49d619]
    /lib/x86_64-linux-gnu/libpthread.so.0(+0xfbb0) [0x7f3b6081cbb0]
    /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x37) [0x7f3b6047bf77]
    /lib/x86_64-linux-gnu/libc.so.6(abort+0x148) [0x7f3b6047f5e8]
    /lib/x86_64-linux-gnu/libc.so.6(+0x2fd43) [0x7f3b60474d43]
    /lib/x86_64-linux-gnu/libc.so.6(+0x2fdf2) [0x7f3b60474df2]
    /usr/lib/x86_64-linux-gnu/libSoundTouch.so.0(+0x9e26) [0x7f3b25c27e26]
    /usr/lib/x86_64-linux-gnu/libSoundTouch.so.0(_ZNK10soundtouch10PeakFinder13getPeakCenterEPKfi+0x7d) [0x7f3b25c27f1d]
    /usr/lib/x86_64-linux-gnu/libSoundTouch.so.0(_ZN10soundtouch10PeakFinder10detectPeakEPKfii+0x67) [0x7f3b25c27ff7]
    /usr/lib/x86_64-linux-gnu/libSoundTouch.so.0(_ZN10soundtouch9BPMDetect6getBpmEv+0x37) [0x7f3b25c27c27]
    /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstsoundtouch.so(+0x4c82) [0x7f3b25e31c82]
    /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(+0x33880) [0x7f3b4a59a880]
    /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(+0x33fc1) [0x7f3b4a59afc1]
    /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(+0x60baa) [0x7f3b4a2c5baa]
    /usr/lib/x86_64-linux-gnu/libgstbase-1.0.so.0(+0x341cb) [0x7f3b4a59b1cb]
    /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(+0x60baa) [0x7f3b4a2c5baa]
    /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(gst_proxy_pad_chain_default+0xbb) [0x7f3b4a2b7d8b]
    /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(+0x60baa) [0x7f3b4a2c5baa]
    /usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(+0x18cbc) [0x7f3b4b080cbc]
    /usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(+0x18f7e) [0x7f3b4b080f7e]
    /usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(gst_audio_decoder_finish_frame+0x442) [0x7f3b4b0854f2]
    /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstvorbis.so(+0x5200) [0x7f3b240ba200]
    /usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(+0x1a743) [0x7f3b4b082743]
    /usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(+0x1ab1b) [0x7f3b4b082b1b]
    /usr/lib/x86_64-linux-gnu/libgstaudio-1.0.so.0(+0x1bc06) [0x7f3b4b083c06]
    /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(+0x60baa) [0x7f3b4a2c5baa]
    /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstcoreelements.so(+0x1d8f1) [0x7f3b34af08f1]
    /usr/lib/x86_64-linux-gnu/libgstreamer-1.0.so.0(+0x8e189) [0x7f3b4a2f3189]
    /lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x6daa6) [0x7f3b5d74daa6]
    /lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x6d0e5) [0x7f3b5d74d0e5]
    /lib/x86_64-linux-gnu/libpthread.so.0(+0x7f6e) [0x7f3b60814f6e]
    /lib/x86_64-linux-gnu/libc.so.6(clone+0x6d) [0x7f3b6053f9cd]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
No threads.

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)



What can I do to fix this?  I'm a bit of a noob so thorough instructions may be necessary.

Thanks!

---

### Post by skimtneer on 2013-10-25
I am not an expert on it, but my first shot would be just to uninstall Banshee completely and reinstall it.

---

