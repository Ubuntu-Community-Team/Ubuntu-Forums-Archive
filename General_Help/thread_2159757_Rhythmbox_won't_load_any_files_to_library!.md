---
title: "Rhythmbox won't load any files to library!"
date: 2013-07-04
forum: General Help
---

### Post by bmfc187 on 2013-07-04
Hello all, trying to figure out what's going here... I have an HP Pavilion g7 laptop, dual booting WIndows 8 and Ubuntu 12.10 64-bit in both in UEFI mode. A little background (skip to next paragraph for the actual problem):  I bought this machine about two or three months ago, i had installed ubuntu on it successfully when i first got it and had been using it fine up until a week or two ago,  Then for some reason i decided to boot into widows, which i rarely, if ever, do.  Well my windows woiuldnt boot and i tried to fix it but i couldnt ever figure it out so i thought, screw it, i never use windows, ill just delete it and install ubuntu on the whole machine.  Now normally this would work fine but being that i have a UEFI machine, i messed up big time.  It erased the EFI partition and rendered ubuntu unbootable.  so i turned my new laptop into a paperweight.  Had to pay almost $20 to have HP send me a recovery disc.  I got the disc, recovered windows 8, then re-installed ubuntu 12.10.  I got it all correct this time and both windows and ubuntu are booting fine.

Now here's the problem.  I always use rhythmbox music player, and it always works fine for me, never had any problems with it until now.  But this time it didn't work.  The first time i opened up rhythmbox, it failed to load ANY of my music files.  It continues to do this every time i open it, i cannot get it to load a single file.  When i look at the "import errors" tab all the files say "The connection is closed." in the "error" column.  The only thing i can think that i did differently from any other time i install ubuntu on a machine, is i installed Audacious music player, for some reason, and opened it before the first time i opened rhythmbox.  I dont know why that would make a difference, but who knows? lol  So Audacious imported ALL of my music just fine, no problems whatsoever, but then when i went to use rhythmbox it wouldnt load ANY of them.  My library is blank.  I even uninstalled rhythmbox and rebooted and then re-installed rhythmbox and i get the same thing. 

 I have never had this problem before, and extensive googling was no help.  Has anyone else ever experienced or even HEARD of this? Hopefully someone can help! It's not that big of a deal, because i have Audacious working well and i like that i can make my own skins for it like winamp, so im not hurting, but I CANT STAND knowing that something doesnt work! I must fix it! lol so if anyone can help me out thatd be awesome! Thanks in advance!

-bmfc

---

### Post by zero2xiii on 2013-07-04
Hay,

Not sure what might be causing the issue so a little more info might help.

Please open rhythmbox from terminal with debug enabled to see more detailed errors.. Please only try and import a single file or only a few so we do not have hundreds of lines of output:
```
rhythmbox --debug #or just -d
```

Please supply us the output AFTER you tried importing a file to your library so we can hopefully see more details about the actual problem.

Thanks :)

---

### Post by bmfc187 on 2013-07-05
Hi, here is the output from "rhythmbox -d"...

```
** (rhythmbox:23053): WARNING **: Error checking for MP3 support: no element "uridecodebin"
(07:55:15) [0x1ddd440] [sync_window_settings] rb-shell.c:2243: paned position 160
(07:55:15) [0x1ddd440] [sync_window_settings] rb-shell.c:2250: right_paned position 400
(07:55:15) [0x1ddd440] [sync_window_settings] rb-shell.c:2257: sidebar paned position 300
(07:55:17) [0x1ddd440] [sync_window_settings] rb-shell.c:2243: paned position 160
(07:55:17) [0x1ddd440] [sync_window_settings] rb-shell.c:2250: right_paned position 400
(07:55:17) [0x1ddd440] [sync_window_settings] rb-shell.c:2257: sidebar paned position 300
(07:55:18) [0x1ddd440] [sync_window_settings] rb-shell.c:2243: paned position 160
(07:55:18) [0x1ddd440] [sync_window_settings] rb-shell.c:2250: right_paned position 400
(07:55:18) [0x1ddd440] [sync_window_settings] rb-shell.c:2257: sidebar paned position 300
(07:55:19) [0x1ddd440] [sync_window_settings] rb-shell.c:2243: paned position 160
(07:55:19) [0x1ddd440] [sync_window_settings] rb-shell.c:2250: right_paned position 400
(07:55:19) [0x1ddd440] [sync_window_settings] rb-shell.c:2257: sidebar paned position 300
(07:55:21) [0x1ddd440] [rb_music_dir] rb-file-helpers.c:194: user music dir: /home/bmfc/Music

** (rhythmbox:23053): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/ipc/linux.py", line 756, in get_info
    return self.service.folders.get_info(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 166, in inner
    result = f(*new_args, **new_kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/logger.py", line 283, in inner
    res = f(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 721, in get_info
    mdobj = self.fs_manager.get_by_path(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 795, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/bmfc/.ubuntuone/Purchased from Ubuntu One'


** (rhythmbox:23053): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed
(07:55:23) [0x1ddd440] [sync_window_settings] rb-shell.c:2243: paned position 160
(07:55:23) [0x1ddd440] [sync_window_settings] rb-shell.c:2250: right_paned position 400
(07:55:23) [0x1ddd440] [sync_window_settings] rb-shell.c:2257: sidebar paned position 300
(07:55:24) [0x1ddd440] [rb_uri_could_be_podcast] rb-file-helpers.c:576: 'file:///home/bmfc/Music' can't be a Podcast or OPML file, not the right scheme
(07:55:24) [0x1ddd440] [rb_shell_load_uri] rb-shell.c:3671: adding uri file:///home/bmfc/Music, play 0
(07:55:24) [0x1ddd440] [load_uri_parser_finished_cb] rb-shell.c:3554: file:///home/bmfc/Music ignored
(07:55:24) [0x1ddd440] [rb_shell_guess_source_for_uri] rb-shell.c:3408: source Play Queue returned strength 25 for uri file:///home/bmfc/Music
(07:55:24) [0x1ddd440] [rb_shell_guess_source_for_uri] rb-shell.c:3408: source Music returned strength 50 for uri file:///home/bmfc/Music
(07:55:24) [0x1ddd440] [load_uri_parser_finished_cb] rb-shell.c:3600: just adding file:///home/bmfc/Music to source Music
(07:55:24) [0x1ddd440] [maybe_create_import_job] rb-library-source.c:1712: creating new import job
(07:55:24) [0x1ddd440] [impl_add_uri] rb-library-source.c:1780: adding uri file:///home/bmfc/Music to library
(07:55:24) [0x1ddd440] [load_uri_finish] rb-shell.c:3517: didn't want to do anything anyway
(07:55:24) [0x1ddd440] [window_focus_cb] rb-mmkeys-plugin.c:169: window got focus, re-grabbing media keys
(07:55:25) [0x1ddd440] [start_import_job] rb-library-source.c:1698: starting import job
(07:55:25) [0x1ddd440] [rhythmdb_import_job_start] rhythmdb-import-job.c:345: starting
(07:55:25) [0x1ddd440] [next_uri] rhythmdb-import-job.c:320: scanning uri file:///home/bmfc/Music
(07:55:25) [0x1ddd440] [uri_recurse_func] rhythmdb-import-job.c:278: waiting for entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/07%20-%20War%20Toy.mp3
(07:55:25) [0x1ddd440] [rhythmdb_add_uri_with_types] rhythmdb.c:2998: queueing stat for "file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/07%20-%20War%20Toy.mp3"...

...(07:55:30) [0x1ddd440] [rhythmdb_add_import_error_entry] rhythmdb.c:2216: adding import error type import-error for file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/07%20-%20War%20Toy.mp3: The connection is closed
(07:55:30) [0x1ddd440] [rhythmdb_entry_new] rhythmdb.c:1767: emitting entry added
(07:55:30) [0x1ddd440] [rhythmdb_process_one_event] rhythmdb.c:2507: processing RHYTHMDB_EVENT_METADATA_LOAD
(07:55:30) [0x1ddd440] [rhythmdb_add_import_error_entry] rhythmdb.c:2216: adding import error type import-error for file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/16%20-%20Rock%20&%20Roll%20Party%20Town.mp3: The connection is closed
(07:55:30) [0x1ddd440] [rhythmdb_entry_new] rhythmdb.c:1767: emitting entry added
(07:55:30) [0x1ddd440] [rhythmdb_process_one_event] rhythmdb.c:2507: processing RHYTHMDB_EVENT_METADATA_LOAD
(07:55:30) [0x1ddd440] [rhythmdb_add_import_error_entry] rhythmdb.c:2216: adding import error type import-error for file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/05%20-%20Slutman%20City.mp3: The connection is closed
(07:55:30) [0x1ddd440] [rhythmdb_entry_new] rhythmdb.c:1767: emitting entry added
(07:55:30) [0x1ddd440] [rhythmdb_process_one_event] rhythmdb.c:2507: processing RHYTHMDB_EVENT_METADATA_LOAD
(07:55:30) [0x1ddd440] [rhythmdb_add_import_error_entry] rhythmdb.c:2216: adding import error type import-error for file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/cover.jpg: The connection is closed
(07:55:30) [0x1ddd440] [rhythmdb_entry_new] rhythmdb.c:1767: emitting entry added
(07:55:30) [0x1ddd440] [rhythmdb_process_one_event] rhythmdb.c:2507: processing RHYTHMDB_EVENT_METADATA_LOAD
(07:55:30) [0x1ddd440] [rhythmdb_add_import_error_entry] rhythmdb.c:2216: adding import error type import-error for file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/03%20-%20Americanized.mp3: The connection is closed
(07:55:30) [0x1ddd440] [rhythmdb_entry_new] rhythmdb.c:1767: emitting entry added
(07:55:30) [0x301eca0] [action_thread_main] rhythmdb.c:2866: executing RHYTHMDB_ACTION_LOAD for "file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/15%20-%20U%20Aint%20Shit.mp3"
(07:55:30) [0x301eca0] [kill_metadata_service] rb-metadata-dbus-client.c:151: dbus connection already closed
(07:55:30) [0x301eca0] [kill_metadata_service] rb-metadata-dbus-client.c:158: killing child process
(07:55:30) [0x301eca0] [kill_metadata_service] rb-metadata-dbus-client.c:165: closing metadata child process stdout pipe
(07:55:30) [0x1ddd440] [rhythmdb_process_one_event] rhythmdb.c:2507: processing RHYTHMDB_EVENT_METADATA_LOAD
(07:55:30) [0x1ddd440] [rhythmdb_add_import_error_entry] rhythmdb.c:2216: adding import error type import-error for file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/12%20-%20Bone%20Meal.mp3: The connection is closed
(07:55:30) [0x1ddd440] [rhythmdb_entry_new] rhythmdb.c:1767: emitting entry added
(07:55:30) [0x1ddd440] [rb_statusbar_sync_status] rb-statusbar.c:467: updating status with: '0 songs', 'Importing (0/2477)', 0.000000
(07:55:30) [0x7e3830] [rb_debug_init_match] rb-debug.c:240: Debugging enabled
(07:55:30) [0x7e3830] [main] rb-metadata-dbus-service.c:371: initializing metadata service; pid = 23148; address = unix:tmpdir=/tmp
(07:55:30) [0x7e3830] [rb_metadata_init] rb-metadata-gst.c:980: giostreamsink not found, can't tag anything
(07:55:30) [0x7e3830] [main] rb-metadata-dbus-service.c:403: D-BUS server listening on address unix:abstract=/tmp/dbus-u9goIMQS
(07:55:30) [0x301eca0] [start_metadata_service] rb-metadata-dbus-client.c:292: Got metadata helper D-BUS address unix:abstract=/tmp/dbus-u9goIMQS
(07:55:30) [0x301eca0] [start_metadata_service] rb-metadata-dbus-client.c:308: Metadata process 23148 started
(07:55:30) [0x7e3830] [new_connection_cb] rb-metadata-dbus-service.c:229: new connection to metadata service
(07:55:30) [0x7e3830] [handle_method_call] rb-metadata-dbus-service.c:193: handling metadata service message: org.gnome.Rhythmbox3.Metadata.getSaveableTypes
(07:55:30) [0x301eca0] [start_metadata_service] rb-metadata-dbus-client.c:334: saveable types from metadata helper: 
(07:55:30) [0x301eca0] [rb_metadata_load] rb-metadata-dbus-client.c:395: sending metadata load request: file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/15%20-%20U%20Aint%20Shit.mp3
(07:55:30) [0x7e3830] [handle_method_call] rb-metadata-dbus-service.c:193: handling metadata service message: org.gnome.Rhythmbox3.Metadata.load
(07:55:30) [0x7e3830] [rb_metadata_dbus_load] rb-metadata-dbus-service.c:74: loading metadata from file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/15%20-%20U%20Aint%20Shit.mp3...

...(rhythmbox-metadata:23148): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/cover.jpg; 1 now imported
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/16%20-%20Rock%20&%20Roll%20Party%20Town.mp3; 2 now imported
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/12%20-%20Bone%20Meal.mp3; 3 now imported
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/05%20-%20Slutman%20City.mp3; 4 now imported
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/07%20-%20War%20Toy.mp3; 5 now imported
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/03%20-%20Americanized.mp3; 6 now imported
(07:55:30) [0x1ddd440] [emit_status_changed] rhythmdb-import-job.c:201: emitting status changed: 6/2477
(07:55:30) [0x1ddd440] [rb_statusbar_page_status_changed_cb] rb-statusbar.c:544: source status changed
(07:55:30) [0x1ddd440] [expand_rows_cb] rb-display-page-tree.c:413: expanding 1 rows
(07:55:30) [0x301eca0] [action_thread_main] rhythmdb.c:2866: executing RHYTHMDB_ACTION_LOAD for "file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/13%20-%20Ollie%20North.mp3"
(07:55:30) [0x1ddd440] [rhythmdb_process_one_event] rhythmdb.c:2507: processing RHYTHMDB_EVENT_METADATA_LOAD
(07:55:30) [0x1ddd440] [rhythmdb_add_import_error_entry] rhythmdb.c:2216: adding import error type import-error for file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/15%20-%20U%20Aint%20Shit.mp3: The connection is closed
(07:55:30) [0x1ddd440] [rhythmdb_entry_new] rhythmdb.c:1767: emitting entry added
(07:55:30) [0x301eca0] [kill_metadata_service] rb-metadata-dbus-client.c:151: dbus connection already closed
(07:55:30) [0x301eca0] [kill_metadata_service] rb-metadata-dbus-client.c:158: killing child process
(07:55:30) [0x301eca0] [kill_metadata_service] rb-metadata-dbus-client.c:165: closing metadata child process stdout pipe
(07:55:30) [0x174c830] [rb_debug_init_match] rb-debug.c:240: Debugging enabled
(07:55:30) [0x174c830] [main] rb-metadata-dbus-service.c:371: initializing metadata service; pid = 23155; address = unix:tmpdir=/tmp
(07:55:30) [0x174c830] [rb_metadata_init] rb-metadata-gst.c:980: giostreamsink not found, can't tag anything
(07:55:30) [0x174c830] [main] rb-metadata-dbus-service.c:403: D-BUS server listening on address unix:abstract=/tmp/dbus-mhq3hLSj
(07:55:30) [0x301eca0] [start_metadata_service] rb-metadata-dbus-client.c:292: Got metadata helper D-BUS address unix:abstract=/tmp/dbus-mhq3hLSj
(07:55:30) [0x301eca0] [start_metadata_service] rb-metadata-dbus-client.c:308: Metadata process 23155 started
(07:55:30) [0x174c830] [new_connection_cb] rb-metadata-dbus-service.c:229: new connection to metadata service
(07:55:30) [0x174c830] [handle_method_call] rb-metadata-dbus-service.c:193: handling metadata service message: org.gnome.Rhythmbox3.Metadata.getSaveableTypes
(07:55:30) [0x301eca0] [start_metadata_service] rb-metadata-dbus-client.c:334: saveable types from metadata helper: 
(07:55:30) [0x301eca0] [rb_metadata_load] rb-metadata-dbus-client.c:395: sending metadata load request: file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/13%20-%20Ollie%20North.mp3
(07:55:30) [0x174c830] [handle_method_call] rb-metadata-dbus-service.c:193: handling metadata service message: org.gnome.Rhythmbox3.Metadata.load
(07:55:30) [0x174c830] [rb_metadata_dbus_load] rb-metadata-dbus-service.c:74: loading metadata from file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/13%20-%20Ollie%20North.mp3...

...(rhythmbox-metadata:23232): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed
(07:55:33) [0x1ddd440] [rb_statusbar_sync_status] rb-statusbar.c:467: updating status with: '0 songs', 'Importing (17/2477)', 0.006863
(07:55:33) [0x1ddd440] [rb_shell_quit] rb-shell.c:3060: Quitting
(07:55:33) [0x1ddd440] [rb_shell_player_stop] rb-shell-player.c:3188: stopping
(07:55:33) [0x1ddd440] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3124: setting playing source to (nil)
(07:55:33) [0x1ddd440] [rb_shell_player_sync_with_source] rb-shell-player.c:2948: playing source: (nil), active entry: (nil)
(07:55:33) [0x1ddd440] [rb_shell_set_window_title] rb-shell.c:2686: clearing title
(07:55:33) [0x1ddd440] [rb_shell_player_sync_buttons] rb-shell-player.c:3039: syncing with source 0x1eee430
(07:55:33) [0x1ddd440] [rb_shell_playing_source_changed_cb] rb-shell.c:2573: playing source changed
(07:55:33) [0x1ddd440] [playing_source_changed_cb] rb-mpris-plugin.c:1286: emitting CanPause change
(07:55:33) [0x1ddd440] [playing_source_changed_cb] rb-mpris-plugin.c:1289: emitting ActivePlaylist change
(07:55:33) [0x1ddd440] [rb_shell_player_sync_with_source] rb-shell-player.c:2948: playing source: (nil), active entry: (nil)
(07:55:33) [0x1ddd440] [rb_shell_set_window_title] rb-shell.c:2686: clearing title
(07:55:33) [0x1ddd440] [playing_entry_changed_cb] rb-mpris-plugin.c:1210: emitting Metadata and CanSeek changed
(07:55:33) [0x1ddd440] [rb_audioscrobbler_song_changed_cb] rb-audioscrobbler.c:1066: called with no playing entry
(07:55:33) [0x1ddd440] [rb_audioscrobbler_song_changed_cb] rb-audioscrobbler.c:1066: called with no playing entry
(07:55:33) [0x1ddd440] [playing_changed_cb] rb-mpris-plugin.c:1190: emitting PlaybackStatus change
(07:55:33) [0x1ddd440] [rb_shell_player_sync_buttons] rb-shell-player.c:3039: syncing with source 0x1eee430
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Tray Icon
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Internet Radio
(07:55:33) [0x1ddd440] [rb_shell_display_page_deleted_cb] rb-shell.c:2533: display page deleted
(07:55:33) [0x1ddd440] [impl_dispose] rb-display-page.c:579: Disposing page Radio
(07:55:33) [0x1ddd440] [rhythmdb_property_model_dispose] rhythmdb-property-model.c:519: disposing property model 0x2a1dcf0
(07:55:33) [0x1ddd440] [rhythmdb_property_model_finalize] rhythmdb-property-model.c:546: finalizing property model 0x2a1dcf0
(07:55:33) [0x1ddd440] [rb_source_finalize] rb-source.c:362: Unreffing model 0x21dd6f0 count: 1
(07:55:33) [0x1ddd440] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x21dd6f0
(07:55:33) [0x1ddd440] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x21dd6f0
(07:55:33) [0x1ddd440] [impl_finalize] rb-display-page.c:597: finalizing page Radio
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Portable Players
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Audio CD Recorder
(07:55:33) [0x1ddd440] [impl_deactivate] rb-disc-recorder-plugin.c:739: RBDiscRecorderPlugin deactivating
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Cover art search
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension MediaServer2 D-Bus interface
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Last.fm
(07:55:33) [0x1ddd440] [impl_delete_thyself] rb-audioscrobbler-profile-page.c:1870: deleting profile page
(07:55:33) [0x1ddd440] [rb_shell_display_page_deleted_cb] rb-shell.c:2533: display page deleted
(07:55:33) [0x1ddd440] [rb_audioscrobbler_dispose] rb-audioscrobbler.c:356: disposing audioscrobbler
(07:55:33) [0x1ddd440] [rb_audioscrobbler_finalize] rb-audioscrobbler.c:401: Finalizing Audioscrobbler
(07:55:33) [0x1ddd440] [impl_dispose] rb-display-page.c:579: Disposing page Last.fm
(07:55:33) [0x1ddd440] [impl_finalize] rb-display-page.c:597: finalizing page Last.fm
(07:55:33) [0x1ddd440] [impl_delete_thyself] rb-audioscrobbler-profile-page.c:1870: deleting profile page
(07:55:33) [0x1ddd440] [rb_shell_display_page_deleted_cb] rb-shell.c:2533: display page deleted
(07:55:33) [0x1ddd440] [rb_audioscrobbler_dispose] rb-audioscrobbler.c:356: disposing audioscrobbler
(07:55:33) [0x1ddd440] [rb_audioscrobbler_finalize] rb-audioscrobbler.c:401: Finalizing Audioscrobbler
(07:55:33) [0x1ddd440] [impl_dispose] rb-display-page.c:579: Disposing page Libre.fm
(07:55:33) [0x1ddd440] [impl_finalize] rb-display-page.c:597: finalizing page Libre.fm
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Ubuntu One
(07:55:33) [0x1ddd440] [rb_shell_display_page_deleted_cb] rb-shell.c:2533: display page deleted
(07:55:33) [0x1ddd440] [update_group_visibility] rb-display-page-model.c:561: page group Stores changing visibility from 1 to 0
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension MPRIS D-Bus interface
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Portable Players - MTP
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Audio CD Player
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension DAAP Music Sharing
(07:55:33) [0x1ddd440] [impl_deactivate] rb-daap-plugin.c:260: Shutting down DAAP plugin
(07:55:33) [0x1ddd440] [stop_browsing] rb-daap-plugin.c:557: Destroying DAAP source lookup
(07:55:33) [0x1ddd440] [libdmapsharing_debug] rb-daap-plugin.c:617: Finalizing DMAPShare
(07:55:33) [0x1ddd440] [libdmapsharing_debug] rb-daap-plugin.c:617: Stopping music sharing server on port 3689
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Portable Players - iPod
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Notification
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Power Manager
(07:55:33) [0x1ddd440] [extension_removed_cb] rb-shell.c:911: deactivating extension Media Player Keys
(07:55:33) [0x1ddd440] [rb_shell_sync_state] rb-shell.c:1817: saving playlists
(07:55:33) [0x1ddd440] [rb_shell_sync_state] rb-shell.c:1821: saving db
(07:55:33) [0x1ddd440] [rhythmdb_save] rhythmdb.c:3184: saving the rhythmdb and blocking
(07:55:33) [0x1ddd440] [rhythmdb_save_async] rhythmdb.c:3166: saving the rhythmdb in the background
(07:55:33) [0x1ddd440] [rhythmdb_read_enter] rhythmdb.c:1228: counter: 1
(07:55:33) [0x23fcc00] [rhythmdb_save_thread_main] rhythmdb.c:3114: entering save thread
(07:55:33) [0x23fcc00] [rhythmdb_save_thread_main] rhythmdb.c:3132: saving rhythmdb
(07:55:33) [0x23fcc00] [save_entry_type] rhythmdb-tree.c:1187: saving entries of type ignore
(07:55:33) [0x23fcc00] [save_entry_type] rhythmdb-tree.c:1187: saving entries of type podcast-feed
(07:55:33) [0x23fcc00] [save_entry_type] rhythmdb-tree.c:1187: saving entries of type song
(07:55:33) [0x23fcc00] [save_entry_type] rhythmdb-tree.c:1187: saving entries of type podcast-post
(07:55:33) [0x23fcc00] [save_entry_type] rhythmdb-tree.c:1187: saving entries of type iradio
(07:55:33) [0x1ddd440] [rhythmdb_save] rhythmdb.c:3201: done
(07:55:33) [0x301eca0] [action_thread_main] rhythmdb.c:2866: executing RHYTHMDB_ACTION_LOAD for "file:///home/bmfc/Music/GWAR/1999%20-%20We%20Kill%20Everything/17%20-%20****in'%20An%20Animal.mp3"
(07:55:33) [0x301eca0] [kill_metadata_service] rb-metadata-dbus-client.c:151: dbus connection already closed
(07:55:33) [0x301eca0] [kill_metadata_service] rb-metadata-dbus-client.c:158: killing child process
(07:55:33) [0x301eca0] [kill_metadata_service] rb-metadata-dbus-client.c:165: closing metadata child process stdout pipe
(07:55:33) [0x2454830] [rb_debug_init_match] rb-debug.c:240: Debugging enabled
(07:55:33) [0x2454830] [main] rb-metadata-dbus-service.c:371: initializing metadata service; pid = 23240; address = unix:tmpdir=/tmp
(07:55:33) [0x2454830] [rb_metadata_init] rb-metadata-gst.c:980: giostreamsink not found, can't tag anything
(07:55:33) [0x2454830] [main] rb-metadata-dbus-service.c:403: D-BUS server listening on address unix:abstract=/tmp/dbus-nExP9Pyd
(07:55:48) [0x2454830] [electromagnetic_shotgun] rb-metadata-dbus-service.c:176: shutting down (1373028948s idle)
```


I tried to cut it down as much as possible, sorry if it is still a little long. 

-bmfc

---

### Post by zero2xiii on 2013-07-05
Hay,

Interesting the amount of errors.. Like really a LOT... However, it still remains somewhat ambiguous... hmm.. It even looks like at some point it successfully imported a few songs:

```
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/cover.jpg; 1 now imported
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/16%20-%20Rock%20&%20Roll%20Party%20Town.mp3; 2 now imported
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/12%20-%20Bone%20Meal.mp3; 3 now imported
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/05%20-%20Slutman%20City.mp3; 4 now imported
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/07%20-%20War%20Toy.mp3; 5 now imported
(07:55:30) [0x1ddd440] [rb_entry_view_row_inserted_cb] rb-entry-view.c:2120: row added
(07:55:30) [0x1ddd440] [entry_added_cb] rhythmdb-import-job.c:447: got entry file:///home/bmfc/Music/GWAR/1988%20-%20Hell-o!/03%20-%20Americanized.mp3; 6 now imported
```

Not sure though, I might be miss understanding the output...

Just to be sure, have you installed all the codecs and such? Easiest way (so I hear) is to install VLC

```
sudo apt-get install vlc
```

I personally prefer to install all restricted extras:

```
sudo apt-get install ubuntu-restricted-extras
```

Give that a shot first. If you have not installed any codecs yet, or maybe are unsure.

Cheers and  good luck.

---

### Post by bmfc187 on 2013-07-09
> **zero2xiii said:**
> Hay,
It even looks like at some point it successfully imported a few songs

Yes it says "add" but nothing ever gets added to library.

> Easiest way (so I hear) is to install VLC

```
sudo apt-get install vlc
```

I personally prefer to install all restricted extras:

```
sudo apt-get install ubuntu-restricted-extras
```

Give that a shot first. If you have not installed any codecs yet, or maybe are unsure.

Cheers and  good luck.

I already had vlc installed, I installed the restricted extras package and nothing seemed to change.

-bmfc

---

### Post by bmfc187 on 2013-07-10
ah, okay i never figured out what the problem was, so i just reinstalled ubuntu and it works now...dont know what it could have been but its better now.  I find that a fresh install fixes alot of problems lol.  Thanks for trying to help!  

-bmfc

---

