---
title: "General Madness... Amarok and id3 tags"
date: 2007-04-05
forum: General Help
---

### Post by Drain on 2007-04-05
I've been scouring Google and past forum posts, trying to figure out what I can do to get this working - any suggestions welcome.

I'm using Amarok as my main music player.  I've got a modest collection of mp3s (about 4000 songs), that are well-tagged, and organized by filename (obsessively ordered as well).  When I play them from my local hard drive, the tags display correctly.  

However, my desktop computer has limited storage.  My fileserver has much more.  So what I end up doing is moving these mp3s onto my fileserver, and mounting a "music" directory using samba.  The mp3s play just fine, but Amarok no longer displays the correct id3 tag information, it displays the filename in the "Title" column, and the rest of the information is blank.  Strangely, it shows the first 2500 items or so correctly, but the last 500 or so songs I've added do not display correctly.  Any suggestions as to what I can do to get Amarok to read the files correctly?


(Just as an experiment, I've deleted the SQLite files under /$home/.kde/share/apps/amarok, to see if I could clear the database, to no avail.)

---

### Post by Falcorian on 2007-04-05
Do the tags reappair if you move a file back to where it was?

If not... I'd guess the tags were either not written to the files (and just stored in a database maybe?), or they got wiped in the move. If they do, then maybe it's an amarok bug reading remote tags.

---

### Post by Drain on 2007-04-06
I re-named the tags of the files with Audio Tag Tool, and they read fine in that program.  The id3 tags read fine in (some) other programs, like in XMMS.  It just seems that Amarok has "decided" not to refresh itself with the new information for the new songs, and is "being lazy" in not showing the id3 tags.*


*I'm sorry for athropomorphizing my computer and Amarok. Just frustrated. ;-)

---

### Post by Falcorian on 2007-04-07
Hmm...

Could Audio Tag Tool have changed the format to something Amarok doesn't like? Seems unlikely... But I'm afraid I have no solutions for you, just grasping at straws. ;)

---

### Post by spankymasterc on 2007-04-07
Hey man you should try songbird if your interested pm me or search media player in forums (tutorials & tips)

---

