---
title: "Samba Processes"
date: 2016-04-23
forum: General Help
---

### Post by mistcloud-misty on 2016-04-23
Since upgrading I keep getting random samba processes that eat up 30+% of my GPU and cause my laptop temperature to fly into 70s while browsing normal. Killing the process works temporarily until it starts back up again. I don't know why these processes are occurring - as far as I know, Samba is only for 'sharing' between network computers. The printer is not set up with Samba, either. 

I want to clarify before I purge Samba to stop these processes that Samba isn't needed for anything essential. (I do not plan on sharing files between network users). I did not have any random samba processes popping up on 15.10, any ideas on that?

---

### Post by bab1 on 2016-04-23
> **mistcloud-misty said:**
> Since upgrading I keep getting random samba processes that eat up 30+% of my GPU and cause my laptop temperature to fly into 70s while browsing normal. Killing the process works temporarily until it starts back up again. I don't know why these processes are occurring - as far as I know, Samba is only for 'sharing' between network computers. The printer is not set up with Samba, either. 

I want to clarify before I purge Samba to stop these processes that Samba isn't needed for anything essential. (I do not plan on sharing files between network users). I did not have any random samba processes popping up on 15.10, any ideas on that?
What Samba processes specifically are you talking about?  Have you installed Samba?  If so, for what use?  File sharing is only one of the things that Samba is used for these days.  By default the only samba tools installed are for the Samba client.  These do not spawn any processes at all.

It might help if you also describe a little more precisely the circumstances that cause the laptop to run warm.

---

### Post by mistcloud-misty on 2016-04-24
I have never installed Samba. But when I notice my laptop is running needlessly hot I open system monitor and see gvfsd-smb-something. When it happens again I'll know what the full process name is. I usually just kill it and I notice nothing happen at all with my computer so despite it using high CPU it is not doing anything for me. 

The laptop runs warm for many reasons. I'm running everything (graphics included) off my processor because the Nvidia driver causes a permanent login loop so I'm forced to use noveaou. Watching youtube will cause it to get warm, playing games, etc. Browsing normally is fine, so when my laptop was running hot and I was just doing some research for a paper I checked and saw that process at 38% (at that time). Killed it and laptop cooled right back down. 

I think it might have to do with this, found twice in syslogs around each time the process occurred. 
```
Apr 23 14:51:04 arcane-X555LB gnome-session[1500]: Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: mkdir failed on directory /var/run/samba/msg.lock: Permission denied
Apr 23 14:51:04 arcane-X555LB gnome-session[1500]: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Apr 23 14:51:04 arcane-X555LB gnome-session[1500]: Please ask your system administrator to enable user sharing.
Apr 23 14:51:18 arcane-X555LB org.gnome.zeitgeist.SimpleIndexer[1361]: ** (zeitgeist-fts:1903): WARNING **: Unable to get info on application://nautilus-autostart.desktop
Apr 23 14:54:12 arcane-X555LB org.gnome.zeitgeist.SimpleIndexer[1361]: message repeated 2 times: [ ** (zeitgeist-fts:1903): WARNING **: Unable to get info on application://nautilus-autostart.desktop]
Apr 23 14:55:21 arcane-X555LB org.gtk.vfs.Daemon[1361]: ** (gvfsd:1426): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection timed out
Apr 23 14:55:21 arcane-X555LB org.gtk.vfs.Daemon[1361]: ** (process:2175): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Apr 23 14:59:37 arcane-X555LB org.gtk.vfs.Daemon[1361]: ** (gvfsd:1426): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection timed out
Apr 23 14:59:37 arcane-X555LB org.gtk.vfs.Daemon[1361]: ** (process:2170): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
```

Does Ubuntu think I have samba installed and is trying to use it? 

When I see the process again I'll update with the full name.

---

### Post by bab1 on 2016-04-24
> **mistcloud-misty said:**
> I have never installed Samba. But when I notice my laptop is running needlessly hot I open system monitor and see gvfsd-smb-something. When it happens again I'll know what the full process name is. I usually just kill it and I notice nothing happen at all with my computer so despite it using high CPU it is not doing anything for me. 

The laptop runs warm for many reasons. I'm running everything (graphics included) off my processor because the Nvidia driver causes a permanent login loop so I'm forced to use noveaou. Watching youtube will cause it to get warm, playing games, etc. Browsing normally is fine, so when my laptop was running hot and I was just doing some research for a paper I checked and saw that process at 38% (at that time). Killed it and laptop cooled right back down. 

I think it might have to do with this, found twice in syslogs around each time the process occurred. 
```
Apr 23 14:51:04 arcane-X555LB gnome-session[1500]: Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: mkdir failed on directory /var/run/samba/msg.lock: Permission denied
Apr 23 14:51:04 arcane-X555LB gnome-session[1500]: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Apr 23 14:51:04 arcane-X555LB gnome-session[1500]: Please ask your system administrator to enable user sharing.
Apr 23 14:51:18 arcane-X555LB org.gnome.zeitgeist.SimpleIndexer[1361]: ** (zeitgeist-fts:1903): WARNING **: Unable to get info on application://nautilus-autostart.desktop
Apr 23 14:54:12 arcane-X555LB org.gnome.zeitgeist.SimpleIndexer[1361]: message repeated 2 times: [ ** (zeitgeist-fts:1903): WARNING **: Unable to get info on application://nautilus-autostart.desktop]
Apr 23 14:55:21 arcane-X555LB org.gtk.vfs.Daemon[1361]: ** (gvfsd:1426): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection timed out
Apr 23 14:55:21 arcane-X555LB org.gtk.vfs.Daemon[1361]: ** (process:2175): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Apr 23 14:59:37 arcane-X555LB org.gtk.vfs.Daemon[1361]: ** (gvfsd:1426): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection timed out
Apr 23 14:59:37 arcane-X555LB org.gtk.vfs.Daemon[1361]: ** (process:2170): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
```

Does Ubuntu think I have samba installed and is trying to use it? 

When I see the process again I'll update with the full name.It's not really Ubuntu itself.  It seems like you are having a problem with Unity or GNOME (including gvfs).   None of these are directly related to a running Samba process.  More to the point some are warnings that the Samba server is not configured or running.

---

