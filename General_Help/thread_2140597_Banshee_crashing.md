---
title: "Banshee crashing"
date: 2013-04-30
forum: General Help
---

### Post by samsanchez on 2013-04-30
Hi

I've got a problem with Banshee on Lubuntu 12.10. Basically, it crashes and closes down whenever I try to play a track. When I run it from the terminal and try to play a song, I get the following output:

```
$ banshee
[Info  11:01:11.717] Running Banshee 2.6.0: [Ubuntu 12.10 (linux-gnu, i686) @ 2012-12-12 06:19:16 UTC]
[Info  11:01:12.972] Updating web proxy from GConf
[Warn  11:01:13.060] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  11:01:13.060] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Warn  11:01:13.081] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  11:01:13.081] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  11:01:13.083] All services are started 1.085441
[Info  11:01:13.842] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/

** (Banshee:5400): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (Banshee:5400): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image
[Info  11:01:14.861] nereid Client Started
[Info  11:01:14.990] GStreamer version 0.10.36.0, gapless: True, replaygain: False
[Info  11:01:24.797] Uncached artwork size 37 requested
(!) [ 5426:    0.000] --> Caught signal 24 (unknown origin) <--
Stacktrace:


Native stacktrace:

    banshee() [0x80e6431]
    [0xb772240c]
    [0xb7722424]
    /lib/i386-linux-gnu/libc.so.6(gsignal+0x4f) [0xb75351df]
    /lib/i386-linux-gnu/libc.so.6(abort+0x175) [0xb7538825]
    /usr/lib/i386-linux-gnu/libdirect-1.2.so.9(+0x8d56) [0xa289bd56]
    [0xb772240c]
    [0xb7722424]
    /lib/i386-linux-gnu/libc.so.6(sigsuspend+0x72) [0xb7535622]
    banshee() [0x8229a7b]
    [0xb7722400]
    [0xb7722422]
    /lib/i386-linux-gnu/libpthread.so.0(pthread_cond_wait+0xad) [0xb76bb93d]
    /usr/lib/i386-linux-gnu/pulseaudio/libpulsecommon-2.1.so(pa_cond_wait+0x2b) [0xa7b5ea9b]
    /usr/lib/i386-linux-gnu/libpulse.so.0(pa_threaded_mainloop_wait+0x3e) [0xa7bb433e]
    /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstpulse.so(+0xae01) [0xa7c2ee01]
    /usr/lib/i386-linux-gnu/libgstaudio-0.10.so.0(gst_ring_buffer_commit_full+0xcf) [0xa7bd8c6f]
    /usr/lib/i386-linux-gnu/libgstaudio-0.10.so.0(+0x23031) [0xa7bef031]
    /usr/lib/i386-linux-gnu/libgstbase-0.10.so.0(+0x25639) [0xb49ab639]
    /usr/lib/i386-linux-gnu/libgstbase-0.10.so.0(+0x2950b) [0xb49af50b]
    /usr/lib/i386-linux-gnu/libgstbase-0.10.so.0(+0x29b90) [0xb49afb90]
    /usr/lib/i386-linux-gnu/libgstbase-0.10.so.0(+0x29fee) [0xb49affee]
    /usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0(gst_pad_push+0x298) [0xb48ec0c8]
    /usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0(gst_proxy_pad_chain_default+0xb4) [0xb48d5774]
    /usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0(gst_pad_push+0x298) [0xb48ec0c8]
    /usr/lib/i386-linux-gnu/libgstbase-0.10.so.0(+0x3b0af) [0xb49c10af]
    /usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0(gst_pad_push+0x298) [0xb48ec0c8]
    /usr/lib/i386-linux-gnu/libgstbase-0.10.so.0(+0x3b0af) [0xb49c10af]
    /usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0(gst_pad_push+0x298) [0xb48ec0c8]
    /usr/lib/i386-linux-gnu/libgstbase-0.10.so.0(+0x3b0af) [0xb49c10af]
    /usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0(gst_pad_push+0x298) [0xb48ec0c8]
    /usr/lib/i386-linux-gnu/libgstbase-0.10.so.0(+0x3b0af) [0xb49c10af]
    /usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0(gst_pad_push+0x298) [0xb48ec0c8]
    /usr/lib/i386-linux-gnu/libgstbase-0.10.so.0(+0x3b0af) [0xb49c10af]
    /usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0(gst_pad_push+0x298) [0xb48ec0c8]
    /usr/lib/i386-linux-gnu/gstreamer-0.10/libgstcoreelements.so(+0x2731f) [0xa7c6e31f]
    /usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0(+0x82e10) [0xb4915e10]
    /usr/lib/i386-linux-gnu/libgstreamer-0.10.so.0(+0x83fb8) [0xb4916fb8]
    /lib/i386-linux-gnu/libglib-2.0.so.0(+0x6cce8) [0xb6119ce8]
    /lib/i386-linux-gnu/libglib-2.0.so.0(+0x6c303) [0xb6119303]
    /lib/i386-linux-gnu/libpthread.so.0(+0x6d4c) [0xb76b7d4c]
    /lib/i386-linux-gnu/libc.so.6(clone+0x5e) [0xb75f5dde]

Debug info from gdb:


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)
```

Any help very much appreciated.

---

### Post by samsanchez on 2013-04-30
The following is the output of banshee --debug, when I try to play a song:

```
$ banshee --debug
** Running Mono with --debug   **
[1 Debug 11:34:10.868] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Info  11:34:10.893] Running Banshee 2.6.0: [Ubuntu 12.10 (linux-gnu, i686) @ 2012-12-12 06:19:16 UTC]
[1 Debug 11:34:10.913] Initializing GTK
[1 Debug 11:34:12.559] Post-Initializing GTK
[1 Debug 11:34:12.583] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 11:34:12.586] Using default gconf-base-key
[1 Debug 11:34:12.679] Core service started (DBusServiceManager, 0.001544)
[1 Debug 11:34:12.682] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 11:34:12.690] Core service started (DBusCommandService, 0.009852)
[1 Debug 11:34:12.721] Opened SQLite (version 3.7.13) connection to /home/sam/.config/banshee-1/banshee.db
[1 Debug 11:34:12.722] Core service started (DbConnection, 0.031794)
[1 Debug 11:34:12.729] Database version 45 is up to date
[1 Debug 11:34:12.763] Core service started (PreferenceService, 0.014943)
[1 Debug 11:34:12.769] Core service started (Network, 0.006585)
[1 Debug 11:34:12.770] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 11:34:12.770] Core service started (SourceManager, 0.000806)
[1 Debug 11:34:12.777] Core service started (MediaProfileManager, 0.00035)
[1 Debug 11:34:12.780] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 11:34:12.783] Core service started (PlayerEngine, 0.00582)
[1 Debug 11:34:12.815] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 11:34:12.816] Core service started (PlaybackController, 0.003678)
[1 Debug 11:34:12.823] Starting - Startup Job
[1 Debug 11:34:12.824] Core service started (JobScheduler, 0.007897)
[1 Debug 11:34:12.837] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 11:34:12.904] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 11:34:12.906] Core service started (HardwareManager, 0.081296)
[1 Debug 11:34:12.907] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 11:34:12.909] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 11:34:12.910] Core service started (CollectionIndexerService, 0.004255)
[1 Debug 11:34:12.912] Core service started (SaveTrackMetadataService, 0.001392)
[1 Debug 11:34:12.948] Adding icon theme search path: /usr/share/banshee/icons
[1 Debug 11:34:12.949] Core service started (GtkElementsService, 0.036836)
[1 Debug 11:34:12.950] Core service started (InterfaceActionService, 0.001383)
[1 Debug 11:34:13.068] Extension actions loaded: MetadataFixActions
[1 Debug 11:34:13.069] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 11:34:13.071] Album artwork path set to /home/sam/.cache/media-art
[1 Debug 11:34:13.089] Core service started (ArtworkManager, 0.019933)
[1 Debug 11:34:13.089] Core service started (BookmarksService, 0.000163)
[1 Debug 11:34:13.347] Adding context page lastfm-recommendations
[1 Debug 11:34:13.585] Constructed Nereid interface: 0.460746
[1 Debug 11:34:13.660] Creating new surface cache for 90px images, capped at 0.93 MiB (30 items)
[1 Debug 11:34:13.726] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 11:34:13.726] Core service started (NereidPlayerInterface, 0.626097)
[1 Debug 11:34:13.728] Extension service started (DaapService, 0.001575)
[1 Debug 11:34:13.730] Extension service started (DapService, 0.000911)
[1 Warn  11:34:13.739] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[1 Warn  11:34:13.739] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[1 Debug 11:34:13.749] Extension service started (MprisService, 0.009771)
[1 Debug 11:34:13.752] Extension service started (PodcastService, 0.002515)
[1 Debug 11:34:13.762] Extension service started (CoverArtService, 0.010373)
[1 Debug 11:34:13.769] Extension service started (BpmService, 0.006464)
[1 Debug 11:34:13.794] Extension service started (SoundMenuService, 0.024893)
[1 Debug 11:34:13.819] Extension service started (EmusicService, 0.025153)
[1 Debug 11:34:13.830] Audioscrobbler state: connected
[1 Debug 11:34:13.833] Extension service started (AudioscrobblerService, 0.013977)
[1 Debug 11:34:13.846] Extension service started (AudioCdService, 0.012534)
[1 Debug 11:34:13.847] Extension service started (DvdService, 0.000854)
[1 Info  11:34:13.850] Updating web proxy from GConf
[1 Debug 11:34:13.856] Direct connection, no proxy in use
[1 Debug 11:34:13.870] Extension service started (GnomeService, 0.023628)
[1 Debug 11:34:13.872] Extension service started (AmazonMp3DownloaderService, 0.001976)
[1 Debug 11:34:13.902] Extension service started (GStreamerCoreService, 0.029197)
[1 Warn  11:34:13.904] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[1 Warn  11:34:13.904] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[1 Info  11:34:13.904] All services are started 1.290836
[1 Debug 11:34:14.415] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 11:34:14.661] Extension source loaded: Internet Archive
[1 Debug 11:34:14.677] Extension source loaded: Radio
[1 Debug 11:34:14.735] Extension source loaded: File System Queue
[1 Debug 11:34:14.739] Extension source loaded: Miro Guide
[1 Debug 11:34:14.768] Extension source loaded: Last.fm
[1 Debug 11:34:14.772] Extension source loaded: Now Playing
[1 Debug 11:34:14.794] Extension source loaded: Audiobooks
[1 Debug 11:34:15.064] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 11:34:15.064] Extension source loaded: Play Queue
[1 Info  11:34:15.068] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/
[1 Debug 11:34:15.072] Extension source loaded: Amazon MP3 Store
[1 Debug 11:34:15.077] Starting GTK main loop
[1 Debug 11:34:15.107] Growing surface cache for 90px images to 0.99 MiB (32 items)
[1 Debug 11:34:15.248] Creating Pango.Layout, configuring Cairo.Context

** (Banshee:7673): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (Banshee:7673): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image
[1 Debug 11:34:15.311] Creating Pango.Layout, configuring Cairo.Context
[1 Info  11:34:15.485] nereid Client Started
[1 Debug 11:34:15.486] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 11:34:15.500] (libbanshee:player) Audiosink has volume: YES
[1 Debug 11:34:15.519] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 11:34:15.576] Player state change: NotReady -> Ready
[1 Debug 11:34:15.581] Loaded equalizer presets: 0.000198
[1 Debug 11:34:15.585] Selected equalizer: Rock
[1 Debug 11:34:15.589] Player state change: Ready -> Idle
[1 Debug 11:34:15.592] (libbanshee:player) Disabled ReplayGain
[1 Info  11:34:15.594] GStreamer version 0.10.36.0, gapless: True, replaygain: False
[1 Debug 11:34:15.597] Delayed Initializating Banshee.Daap.DaapService
[1 Debug 11:34:15.598] Delayed Initializating Banshee.Dap.DapService
[1 Debug 11:34:15.645] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 11:34:15.646] Dap support extension loaded: Banshee.Dap.Mtp
[1 Debug 11:34:15.647] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 11:34:15.648] Delayed Initializating Banshee.Podcasting.PodcastService
[8 Debug 11:34:15.693] Refreshing any podcasts that haven't been updated in over an hour
[11 Debug 11:34:15.904] DAAP Proxy listening for connections on port 8089
[1 Debug 11:34:16.694] Finished - Startup Job
[1 Debug 11:34:16.698] Starting - Downloading Cover Art
[13 Debug 11:34:16.704] Finished - Downloading Cover Art
[1 Debug 11:34:19.962] Player state change: Idle -> Loading
[1 Debug 11:34:20.189] Player state change: Loading -> Loaded
[1 Debug 11:34:20.198] (libbanshee:player) [gapless] Triggering track-change signal
[1 Info  11:34:20.229] Uncached artwork size 37 requested
[1 Debug 11:34:20.232] Player state change: Loaded -> Playing
[1 Debug 11:34:20.243] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 11:34:20.243] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 11:34:21.251] TrackInfoDisplay RenderAnimation: 32.00 FPS
[1 Debug 11:34:22.926] Starting - Saving Metadata to File
[20 Debug 11:34:22.938] Finished - Saving Metadata to File
(!) [ 7697:    0.000] --> Caught signal 24 (unknown origin) <--
Stacktrace:


Native stacktrace:

(!) [ 7691:    0.000] --> Caught signal 24 (unknown origin) <--
Aborted (core dumped)
```

---

