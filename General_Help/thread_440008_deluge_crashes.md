---
title: "deluge crashes"
date: 2007-05-11
forum: General Help
---

### Post by adza on 2007-05-11
hi there, hoping someone can help me here... deluge installed okay for me, then it started on first instance.. on reboot however, get the following errors...

no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Torrent Size 340820869.0
Available Space 141639143424
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)


huh?

---

### Post by SlackLagg on 2007-05-11
This is a well documented problem with the 0.50 build. 

[http://forum.deluge-torrent.org/viewtopic.php?f=5&t=14&sid=3dc270ea9c5fd34a22aed984fa6f1245](http://forum.deluge-torrent.org/viewtopic.php?f=5&t=14&sid=3dc270ea9c5fd34a22aed984fa6f1245)

discusses this. Apparently the svn build eleminates MOST of the problems that cause this error.  

Basically you just need to delete a file called persistent.state.  I  occasionally make backups up this file so that if I do have a crash, I can just rename my backup to persistent.state and be ready to roll. (I'm thinking about making my own code that will do this automatically, but my python is weak)

Check out 

[http://ubuntuforums.org/showthread.php?t=432101&highlight=deluge](http://ubuntuforums.org/showthread.php?t=432101&highlight=deluge)

 if you'd like Deluge to remember your torrents without having to close the program (very useful if you have a crash or you shutdown machine with Deluge still runnning)

---

