---
title: "Kdenlive snap can't save or load because of AppArmor"
date: 2020-02-03
forum: General Help
---

### Post by dcroxton on 2020-02-03
Xubuntu 19.10, trying to run kdenlive.  The .deb package crashes every time I try to add a clip, so I tried the snap version.  It works well except that it can't load or save anything.

I've seen things about snap apps not being able to load or save to/from removable drives, but that's not the problem here.  It's any drive.  There's not even a dialogue.

There are a lot of error messages on the console, but most of them are pretty much this:

```

org.kde.solid.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.2390\" (uid=1000 pid=12837 comm=\"kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=1256 comm=\"/usr/lib/udisks2/udisksd \" label=\"unconfined\")"
kf5.kio.kio_tags: tag fetch failed: "Failed to open the database"

```

I tried my usual quick workaround of running as root, but it wouldn't let me open a window.  Any idea how I can fix this?

---

### Post by dcroxton on 2020-02-05
No one has any suggestions?

---

### Post by jriddell on 2020-03-19
I've updated kdenlive and you can connect it manually with
snap connect kdenlive:removable-media :removable-media
I'll request the connection gets added automatically

---

### Post by TheFu on 2020-03-19
> **jriddell said:**
> I've updated kdenlive and you can connect it manually with
snap connect kdenlive:removable-media :removable-media
I'll request the connection gets added automatically

With TB of media that needs editing, when will NFS storage mounted  ... er .... anywhere (not $HOME, not under /media/ ) be supported by snaps? Snaps are terribly broken for us until that is fixed, at least for video editors.  Local control for which storage locations can be opened and saved and used for scratch storage by each snap installed is necessary.

For lighter applications, the size of snaps and RAM use breaks them.

The Linux File System Hierarchy standards say that /media/ is for temporary mounts, not permanent.

---

