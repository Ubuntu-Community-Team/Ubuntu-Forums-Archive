---
title: "sound juicer problems"
date: 2005-04-10
forum: General Help
---

### Post by dcast on 2005-04-10
When I rip cds with soundjuicer it doesn't allow me to change the title of the track from say "track 1" to whatever. I tried going into the actual file where the music is stored (not music player) to change the names. however the names changed there and not in the music player juke box  where i organize my music> I noticed that there is no way to change the names in the jukebox either??? Also i was wondering of any plugins were included such as mp3 plugins?

---

### Post by Nis on 2005-04-10
[QUOTE=dcast]When I rip cds with soundjuicer it doesn't allow me to change the title of the track from say "track 1" to whatever. I tried going into the actual file where the music is stored (not music player) to change the names. however the names changed there and not in the music player juke box  where i organize my music> I noticed that there is no way to change the names in the jukebox either??? Also i was wondering of any plugins were included such as mp3 plugins?[/QUOTE]
 If you want mp3 playback in Rhythmbox (Music Player), you'll need to install gstreamer0.8-mad in universe.  Use Synaptic to do this ([search ULF](http://www.ubuntuforums.org/search.php?) for how to do this if need to).  Currently mp3 encoding is not available in universe or multiverse but there are gstreamer0.8-lame packages in marillat (again, [search ULF](http://www.ubuntuforums.org/search.php?) if you need to).  I would suggest encoding to ogg or flac because you'll get better sound and more compatibility on Linux.
For ID3 tag editing install EasyTag (I believe it is in universe).  Rhythmbox does not currently support ID3 tag editing but EasyTag allows you to do simple tag editing and powerful batch editing (editing multiple files at once).  Changing the file name is not enough because the actual track information is stored in the ID3 tag.

---

### Post by dcast on 2005-04-11
Thanks for the help the reason I want mp3 is so that i can listen to it on my portable which doesn't suppoert ogg. I'll try this tonight.

---

