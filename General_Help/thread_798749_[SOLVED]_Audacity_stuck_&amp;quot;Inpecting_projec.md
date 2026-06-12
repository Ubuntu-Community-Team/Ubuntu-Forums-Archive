---
title: "[SOLVED] Audacity stuck &amp;quot;Inpecting project file data...&amp;quot; whilst opening .aup file"
date: 2008-05-18
forum: General Help
---

### Post by peterx14 on 2008-05-18
I recently had a problem where I was recording some music on a laptop running Ubuntu 8.04 with Audacity 1.3.4-beta, and then moving the .aup file to my desktop Ubuntu 7.10 + Audacity 1.3.4-beta. When I tried to open the file on the desktop, Audacity would show a "Progress" dialog saying "Inspecting project file data..." and then hang using up CPU cycles.

Interestingly, running top shows that it is mostly Xorg that's eating CPU time and not so much the Audacity process.

Anyway... to cut a long one short, I was able to resolve the problem by opening the .aup file in a text editor and changing the **h** attribute of the **project** element to the value "0". So for example, with the file starting like this:

```

<?xml version="1.0" standalone="no" ?>
<!DOCTYPE project PUBLIC "-//audacityproject-1.3.0//DTD//EN" "http://audacity.sourceforge.net/xml/audacityproject-1.3.0.dtd" >
<project xmlns="http://audacity.sourceforge.net/xml/" projname="side1_data" version="1.3.0" audacityversion="1.3.4-beta" sel0="0.0000000000" sel1="0.0000000000" vpos="0" h="221.9711564626" zoom="86.1328125000" rate="44100">
    <tags>

```

I changed the bit where it says **h="221.9711564626"** to **h="0"**.

I'm guessing this problem is due to my laptop and desktop computers running at different screen resolutions (1024x768 and 1680x1050 respectively) and a bug where Audacity is trying to scale the cursor position and wave form. Or something?!

Anyway, hopefully this will help someone. I haven't filled a bug with the Audacity folks myself, but if anyone else wants to... please feel free! There is a more recent update however, so this bug may have already been fixed for all I know.

---

### Post by michelepolo on 2008-10-14
i'm not as well as you are, changing as you said initially returned an ampty project (HORROR!!) and the recovering the .aup file gave me an abortion  

 audacity 
*** glibc detected *** audacity: double free or corruption (out): 0xbfa998f8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73b2a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb73b64f0]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7558b11]
/usr/lib/libwx_gtk2u_core-2.6.so.0(_ZN12wxWindowBase15DestroyChildrenEv+0x23)[0xb7a35503]
audacity[0x8106796]
/usr/lib/libwx_baseu-2.6.so.0(_ZNK12wxAppConsole11HandleEventEP12wxEvtHandlerMS0_FvR7wxEventES3_+0x41)[0xb76f37a1]
/usr/lib/libwx_baseu-2.6.so.0(_ZN12wxEvtHandler21ProcessEventIfMatchesERK21wxEventTableEntryBasePS_R7wxEvent+0x8b)[0xb7781f5b]
/usr/lib/libwx_baseu-2.6.so.0(_ZN16wxEventHashTable11HandleEventER7wxEventP12wxEvtHandler+0x78)[0xb77820b8]
/usr/lib/libwx_baseu-2.6.so.0(_ZN12wxEvtHandler12ProcessEventER7wxEvent+0xc2)[0xb7782232]
/usr/lib/libwx_gtk2u_core-2.6.so.0(_ZN12wxWindowBase5CloseEb+0x73)[0xb7a38ec3]
audacity[0x807e257]
audacity[0x807e292]
audacity[0x8192916]
audacity[0x81929bd]
audacity[0x80f9d3b]
/usr/lib/libwx_baseu-2.6.so.0(_ZNK12wxAppConsole11HandleEventEP12wxEvtHandlerMS0_FvR7wxEventES3_+0x41)[0xb76f37a1]
/usr/lib/libwx_baseu-2.6.so.0(_ZN12wxEvtHandler21ProcessEventIfMatchesERK21wxEventTableEntryBasePS_R7wxEvent+0x8b)[0xb7781f5b]
/usr/lib/libwx_baseu-2.6.so.0(_ZN16wxEventHashTable11HandleEventER7wxEventP12wxEvtHandler+0x78)[0xb77820b8]
/usr/lib/libwx_baseu-2.6.so.0(_ZN12wxEvtHandler12ProcessEventER7wxEvent+0xc2)[0xb7782232]
/usr/lib/libwx_gtk2u_core-2.6.so.0[0xb79a3813]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x4f)[0xb6fa7aff]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xb6f9a759]
/usr/lib/libgobject-2.0.so.0[0xb6faef8b]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8ef)[0xb6fb0c1f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb6fb0f69]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_activate+0x58)[0xb723c278]
/usr/lib/libgtk-x11-2.0.so.0(gtk_menu_shell_activate_item+0x182)[0xb7125bc2]
/usr/lib/libgtk-x11-2.0.so.0[0xb7127708]
/usr/lib/libgtk-x11-2.0.so.0[0xb711e914]
/usr/lib/libgtk-x11-2.0.so.0[0xb71188d4]
/usr/lib/libgobject-2.0.so.0[0xb6f99079]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ff)[0xb6f9a82f]
/usr/lib/libgobject-2.0.so.0[0xb6faf11a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x617)[0xb6fb0947]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb6fb0f69]
/usr/lib/libgtk-x11-2.0.so.0[0xb7237667]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0xc1)[0xb7111b21]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x2b8)[0xb7112d88]
/usr/lib/libgdk-x11-2.0.so.0[0xb6e88a9a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x176)[0xb6f15dd6]
/usr/lib/libglib-2.0.so.0[0xb6f19193]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x6e)[0xb6f1974e]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_iteration+0x34)[0xb71130d4]
/usr/lib/libwx_gtk2u_core-2.6.so.0(_ZN5wxApp5YieldEb+0x67)[0xb790ebd7]
/usr/lib/libwx_baseu-2.6.so.0(_Z15wxYieldIfNeededv+0x33)[0xb7784353]
/usr/lib/libwx_gtk2u_core-2.6.so.0(_ZN17wxGenericTreeCtrl8ScrollToERK12wxTreeItemId+0x265)[0xb7a68825]
/usr/lib/libwx_gtk2u_core-2.6.so.0(_ZN17wxGenericTreeCtrl13EnsureVisibleERK12wxTreeItemId+0x70)[0xb7a6bdc0]
/usr/lib/libwx_gtk2u_core-2.6.so.0(_ZN17wxGenericTreeCtrl12DoSelectItemERK12wxTreeItemIdbb+0x1e4)[0xb7a6bfe4]
/usr/lib/libwx_gtk2u_core-2.6.so.0(_ZN17wxGenericTreeCtrl10SelectItemERK12wxTreeItemIdb+0x66)[0xb7a6c186]
audacity[0x824c708]
audacity[0x824ceb5]
audacity[0x822df46]
audacity[0x80cdef4]
audacity[0x8192916]
audacity[0x81929bd]
audacity[0x80f9d3b]
/usr/lib/libwx_baseu-2.6.so.0(_ZNK12wxAppConsole11HandleEventEP12wxEvtHandlerMS0_FvR7wxEventES3_+0x41)[0xb76f37a1]
/usr/lib/libwx_baseu-2.6.so.0(_ZN12wxEvtHandler21ProcessEventIfMatchesERK21wxEventTableEntryBasePS_R7wxEvent+0x8b)[0xb7781f5b]
/usr/lib/libwx_baseu-2.6.so.0(_ZN16wxEventHashTable11HandleEventER7wxEventP12wxEvtHandler+0x78)[0xb77820b8]
/usr/lib/libwx_baseu-2.6.so.0(_ZN12wxEvtHandler12ProcessEventER7wxEvent+0xc2)[0xb7782232]
/usr/lib/libwx_gtk2u_core-2.6.so.0[0xb79a3813]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x4f)[0xb6fa7aff]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xb6f9a759]
======= Memory map: ========
08048000-08494000 r-xp 00000000 08:01 915429     /usr/bin/audacity
08494000-084c8000 rw-p 0044b000 08:01 915429     /usr/bin/audacity
084c8000-0966b000 rw-p 084c8000 00:00 0          [heap]
b3f00000-b3f21000 rw-p b3f00000 00:00 0 
b3f21000-b4000000 ---p b3f21000 00:00 0 
b4060000-b4071000 r--s 00000000 08:01 220390     /usr/share/mime/mime.cache
b4071000-b40d0000 r-xp 00000000 08:01 1054196    /usr/lib/libgio-2.0.so.0.0.0
b40d0000-b40d2000 rw-p 0005e000 08:01 1054196    /usr/lib/libgio-2.0.so.0.0.0
b40d2000-b4104000 r-xp 00000000 08:01 1058042    /usr/lib/libcroco-0.6.so.3.0.1
b4104000-b4107000 rw-p 00031000 08:01 1058042    /usr/lib/libcroco-0.6.so.3.0.1
b4107000-b4137000 r-xp 00000000 08:01 1058002    /usr/lib/libgsf-1.so.114.0.7
b4137000-b413a000 rw-p 0002f000 08:01 1058002    /usr/lib/libgsf-1.so.114.0.7
b413a000-b413b000 rw-p b413a000 00:00 0 
b413b000-b416b000 r-xp 00000000 08:01 1058045    /usr/lib/librsvg-2.so.2.22.2
b416b000-b416c000 rw-p 00030000 08:01 1058045    /usr/lib/librsvg-2.so.2.22.2
b4173000-b4184000 r--s 00000000 08:01 220390     /usr/share/mime/mime.cache
b4184000-b4776000 r--p 00000000 08:01 163866     /usr/share/icons/hicolor/icon-theme.cache
b4776000-b4d68000 r--p 00000000 08:01 163866     /usr/share/icons/hicolor/icon-theme.cache
b4d68000-b4d7c000 r-xp 00000000 08:01 1058432    /usr/lib/libbeagle.so.1.0.0
b4d7c000-b4d7d000 rw-p 00013000 08:01 1058432    /usr/lib/libbeagle.so.1.0.0
b4d7d000-b4db1000 r-xp 00000000 08:01 1053504    /usr/lib/libdbus-1.so.3.4.0
b4db1000-b4db3000 rw-p 00033000 08:01 1053504    /usr/lib/libdbus-1.so.3.4.0
b4db3000-b4dcd000 r-xp 00000000 08:01 1058180    /usr/lib/libdbus-glib-1.so.2.1.0
b4dcd000-b4dce000 rw-p 0001a000 08:01 1058180    /usr/lib/libdbus-glib-1.so.2.1.0
b4dce000-b4dd6000 r-xp 00000000 08:01 939666     /usr/lib/libtrackerclient.so.0.0.0
b4dd6000-b4dd7000 rw-p 00007000 08:01 939666     /usr/lib/libtrackerclient.so.0.0.0
b4dd8000-b4de7000 r-xp 00000000 08:01 865086     /lib/libbz2.so.1.0.4
b4de7000-b4de8000 rw-p 0000f000 08:01 865086     /lib/libbz2.so.1.0.4
b4de8000-b4de9000 r-xp 00000000 08:01 1120818    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b4de9000-b4dea000 rw-p 00000000 08:01 1120818    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b4dea000-b4dee000 r-xp 00000000 08:01 1118205    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b4dee000-b4def000 rw-p 00003000 08:01 1118205    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b4def000-b4e76000 r--p 00000000 08:01 57319      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b4e76000-b4ed6000 rw-s 00000000 00:09 13140001   /SYSV00000000 (deleted)
b4ed6000-b4edc000 r-xp 00000000 08:01 1120838    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b4edc000-b4edd000 rw-p 00005000 08:01 1120838    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b4edd000-b4f6e000 r--p 00000000 08:01 57318      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4f6e000-b4f70000 r-xp 00000000 08:01 1118114    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4f70000-b4f71000 rw-p 00001000 08:01 1118114    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4f71000-b4f72000 r-xp 00000000 08:01 1104563    /usr/lib/ladspa/const_1909.so
b4f72000-b4f73000 rw-p 00000000 08:01 1104563    /usr/lib/ladspa/const_1909.so
b4f73000-b4f75000 r-xp 00000000 08:01 1104782    /usr/lib/ladspa/tap_deesser.so
b4f75000-b4f76000 rw-p 00002000 08:01 1104782    /usr/lib/ladspa/tap_deesser.so
b4f76000-b4f7e000 rw-p b4f76000 00:00 0 
b4f7e000-b4f7f000 r-xp 00000000 08:01 1104510    /usr/lib/ladspa/crossover_dist_1404.so
b4f7f000-b4f80000 rw-p 00000000 08:01 1104510    /usr/lib/ladspa/crossover_dist_1404.so
b4f80000-b4f82000 r-xp 00000000 08:01 1104356    /usr/lib/ladspa/sequencer64_1675.so
b4f82000-b4f83000 rw-p 00001000 08:01 1104356    /usr/lib/ladspa/sequencer64_1675.so
b4f83000-b4f87000 r-xp 00000000 08:01 1104793    /usr/lib/ladspa/tap_reverb.so
b4f87000-b4f8c000 rw-p 00003000 08:01 1104793    /usr/lib/ladspa/tap_reverb.so
b4f8c000-b4f8e000 r-xp 00000000 08:01 1104792    /usr/lib/ladspa/tap_reflector.so
b4f8e000-b4f8f000 rw-p 00002000 08:01 1104792    /usr/lib/ladspa/tap_reflector.so
b4f8f000-b4f90000 rw-p b4f8f000 00:00 0 
b4f90000-b4f91000 r-xp 00000000 08:01 1104523    /usr/lib/ladspa/rate_shifter_1417.so
b4f91000-b4f92000 rw-p 00000000 08:01 1104523    /usr/lib/ladspa/rate_shifter_1417.so
b4f92000-b4f93000 r-xp 00000000 08:01 1104674    /usr/lib/ladspa/adenv_lvl.so
b4f93000-b4f94000 rw-p 00000000 08:01 1104674    /usr/lib/ladspa/adenv_lvl.so
b4f94000-b4f95000 r-xp 00000000 08:01 1104497    /usr/lib/ladspa/valve_1209.so
b4f95000-b4f96000 rw-p 00001000 08:01 1104497    /usr/lib/ladspa/valve_1209.so
b4f96000-b4f98000 r-xp 00000000 08:01 1104351    /usr/lib/ladspa/quantiser50_2028.so
b4f98000-b4f99000 rw-p 00001000 08:01 1104351    /usr/lib/ladspa/quantiser50_2028.so
b4f99000-b4f9b000 r-xp 00000000 08:01 1104359    /usr/lib/ladspa/square_1643.so
b4f9b000-b4f9c000 rw-p 00001000 08:01 1104359    /usr/lib/ladspa/square_1643.so
b4f9c000-b4f9f000 r-xp 00000000 08:01 1104553    /usr/lib/ladspa/dj_eq_1901.so
b4f9f000-b4fa0000 rw-p 00002000 08:01 1104553    /usr/lib/ladspa/dj_eq_1901.so
b4fa0000-b4fa5000 r-xp 00000000 08:01 1104785    /usr/lib/ladspa/tap_dynamics_st.so
b4fa5000-b4fa6000 rw-p 00004000 08:01 1104785    /usr/lib/ladspa/tap_dynamics_st.so
b4fa6000-b4fa8000 r-xp 00000000 08:01 1104357    /usr/lib/ladspa/sequencer32_1676.so
b4fa8000-b4fa9000 rw-p 00001000 08:01 1104357    /usr/lib/ladspa/sequencer32_1676.so
b4fa9000-b4fb1000 r-xp 00000000 08:01 1104487    /usr/lib/ladspa/hermes_filter_1200.so
b4fb1000-b4fb2000 rw-p 00007000 08:01 1104487    /usr/lib/ladspa/hermes_filter_1200.so
b4fb2000-b4fb4000 r-xp 00000000 08:01 1104358    /usr/lib/ladspa/sequencer16_1677.so
b4fb4000-b4fb5000 rw-p 00001000 08:01 1104358    /usr/lib/ladspa/sequencer16_1677.so
b4fb5000-b4fb7000 r-xp 00000000 08:01 1104352    /usr/lib/ladspa/quantiser100_2029.so
b4fb7000-b4fb8000 rw-p 00002000 08:01 1104352    /usr/lib/ladspa/quantiser100_2029.so
b4fb8000-b4fbb000 r-xp 00000000 08:01 1104540    /usr/lib/ladspa/sc4_1882.so
b4fbb000-b4fbc000 rw-p 00002000 08:01 1104540    /usr/lib/ladspa/sc4_1882.so
b4fbc000-b4fbe000 rw-p b4fbc000 00:00 0 
b4fbe000-b4fc0000 r-xp 00000000 08:01 1104544    /usr/lib/ladspa/gong_beater_1439.so
b4fc0000-b4fc1000 rw-p 00001000 08:01 1104544    /usr/lib/ladspa/gong_beater_1439.so
b4fc1000-b4fc2000 r-xp 00000000 08:01 1104485    /usr/lib/ladspa/foverdrive_1196.so
b4fc2000-b4fc3000 rw-p 00000000 08:01 1104485    /usr/lib/ladspa/foverdrive_1196.so
b4fc3000-b4fc7000 r-xp 00000000 08:01 1104558    /usr/lib/ladspa/delay_1898.so
b4fc7000-b4fc8000 rw-p 00003000 08:01 1104558    /usr/lib/ladspa/delay_1898.so
b4fc8000-b4fc9000 r-xp 00000000 08:01 1104535    /usr/lib/ladspa/inv_1429.so
b4fc9000-b4fca000 rw-p 00000000 08:01 1104535    /usr/lib/ladspa/inv_1429.so
b4fca000-b4fcc000 r-xp 00000000 08:01 1104426    /usr/lib/ladspa/filters.so
b4fcc000-b4fcd000 rw-p 00001000 08:01 1104426    /usr/lib/ladspa/filters.so
b4fcd000-b4fce000 r-xp 00000000 08:01 1104519    /usr/lib/ladspa/hard_limiter_1413.so
b4fcAborted

---

