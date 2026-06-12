---
title: "Rhythmbox mp3 ID3 tags problem"
date: 2005-07-10
forum: General Help
---

### Post by lparsons on 2005-07-10
I just setup a new Ubuntu 5.04 box and setup  Samba share for my music files.  The ID3 tags are read fine by my windows machine and even EasyTag on my local Ubuntu box.  However, Rhythmbox imports all of the files without looking at the ID3 tags.  Any ideas on what the problem might be?  Thanks for any help.

---

### Post by doclivingston on 2005-07-11
That's very odd, because RB uses ID3 (and equivalent) tags almost exclusively - it only looks at the filename if there are no ID3 tags at all.

If you run rhythmbox via "rhythmbox -d" in a terminal it will print out debugging information. If you could copy some of the info it prints out, and paste it here, that'd be helpful - you shouldn't need to copy too much, just the info from when it loads one or two mp3s (it will print out a *lot* of stuff).

---

### Post by lparsons on 2005-07-12
It did seem rather strange.  I should also mention that I used WinAmp to put some tags on a FLAC file and they were read OK, however, I believe those are not ID3 tags.  Anyway, here are the relevant lines while it's loading one of the mp3 files:

```
[0x8141a78] [rb_metadata_load] rb-metadata-gst.c:477 (21:14:40): loading metadata for uri: file:///home/Music/Allman%20Brothers%20Band/A%20Decade%20of%20Hits%201969-1979/01-Statesboro%20Blues.mp3
[0x80eacd0] [rb_shell_player_state_changed_cb] rb-shell-player.c:1435 (21:14:41): state changed
[0x80eacd0] [rb_shell_player_sync_control_state] rb-shell-player.c:1377 (21:14:41): syncing control state
[0x80eacd0] [rb_shell_player_sync_buttons] rb-shell-player.c:1684 (21:14:41): syncing with source 0x82bee60
[0x80eacd0] [rb_shell_player_set_play_button] rb-shell-player.c:1577 (21:14:41): setting play button
[0x8141a78] [rb_metadata_gst_typefind_cb] rb-metadata-gst.c:430 (21:14:41): found type application/x-id3
[0x8141a78] [rb_metadata_gst_fakesink_handoff_cb] rb-metadata-gst.c:445 (21:14:41): in fakesink handoff
[0x8141a78] [rb_metadata_load] rb-metadata-gst.c:541 (21:14:41): duration query succeeded
[0x8141a78] [rhythmdb_entry_new] rhythmdb.c:730 (21:14:41): emitting entry added
```

---

### Post by jonspinks on 2005-07-23
Hi,
I recently experienced the same problem.  My mp3 collection lives on my PC and everything is fine there.  However when I was moving MP3's to my laptop Rhythmbox wasn't reading their ID3 tags.  This was strange as I thought I had all of the right libraries in order to decode them (libid3tag etc) and Beep could read them fine.

I installed gstreamer0.8-plugins which gets down all of the available gstreamer plugins.  It was probably most likely gstreamer0.8-mad which sorted it out but I figured that it wouldn't hurt to have all plugins installed.  Anyway the long and short of it is that Rhythmbox now reads the ID3 tags as it should.

Jon

---

### Post by doclivingston on 2005-07-23
gstreamer0.8-mad is what will let you play mp3s and read id3 tags. If it is installed correctly, but Rhythmbox doesn't read the id3 tags, something strange is going on.

---

