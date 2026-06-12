---
title: "USB keys mount at /mount/$user/foo, but USB phones mount at /run/user/1000/gvfs/mtp ?"
date: 2019-07-03
forum: General Help
---

### Post by dankegel on 2019-07-03
Hi!

As [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) says, USB thumb drives are mounted at /mount/$username/foo.  
Splendid, I can cd to that easily.
(Evidently that's done by udisks2.)

Alas, Android phones plugged in via USB are mounted at /run/user/1000/gvfs/mtp:host=foo 
Not splendid, I can never remember that path, can't even find it easily, I end up doing
 find /run -name '*Nokia*'
every time.   It's so obscure that at first I thought they weren't being automounted,
so I kept searching for software to access mtp devices, 
and it always exploded on startup because mtp was already being handled by gnome.
(Evidently that's done by gvfs.)

This feels a bit hostile to commandline users.  Why aren't mtp devices mounted at /mount/$username/foo as $deity intended?
Can that location be configured?

---

### Post by TheFu on 2019-07-03
MTP is a different protocol than usb_storage.  Different teams who don't want to step on each other's toes?
That's just a guess.

You can configure where usb_storage gets mounted use the fstab or autofs.

$deity never intended for any automatic storage mounts in Unix systems.  Only admin/root should have that ability.  gvfs is an abomination as are many other mount tools created by the gnome bloat team.




IMHO.

---

### Post by dankegel on 2019-07-03
I *like* where normal usb storage is mounted.

I don't like where MTP storage is mounted.  Can *that* be configured?

---

### Post by TheFu on 2019-07-04
This has been bothering me too.  The last few months, I've been unable to directly connect my android phone to my laptop.  Today I spent about 30 min trying to manually use mount.mtpfs and mtp-tools go-mtpfs

go-mtpfs is working for me. Let's me manually mount the storage **anywhere** that my userid has permissions.  
```
sudo apt install mtp-tools go-mtpfs
mkdir ~/mtp
chmod 700 ~/mtp   # for security
go-mtpfs ~/mtp
```
BAM!  everything is under ~/mtp/
I haven't automated the mount yet, but it looks like mount.mtpfs is included, so autofs should be able to do that.

The install of go-mtpfs was a monster because I didn't have any development tools on my local system already. It installed g++, lots of golang stuff - about 40 dependencies.  When I switch it over to using autofs, I'll purge the go-mtpfs stuff to clean up all those dependencies.

Be very careful. I used rmdir and it wiped a few directories that had subdirectories inside them.  This is NOT the expected behavior. HUGE BUG!!!  non-empty directories should not be removed by using rmdir.  Damn FUSE file systems.

When you are all finished, use the 
```
fusermount -u ~/mtp
```
to umount it.  You'll need to manually ensure the file system isn't busy anymore, so don't leave any shells open down there and don't be using some file manager to access the directories.

Update:
I never got mtpfs working directly or with autofs.

---

### Post by dankegel on 2019-07-05
Yeah, I've used other tools, but that was before I knew the OS already automounted the MTP device somewhere.

Maybe it's time to file a bug.

---

### Post by TheFu on 2019-07-05
> **dankegel said:**
> Yeah, I've used other tools, but that was before I knew the OS already automounted the MTP device somewhere.

Maybe it's time to file a bug.

Probably not.  It isn't a "bug" as far as the devs are concerned. "Closed: Working as designed." I looked for a way to have it mount somewhere else, not seeing that, I suspect it is buried in dconf or gconf somewhere, if it isn't hard coded.  The "free desktop.org" guys might have something in their documentation. IDK.

My OS doesn't automount anything.  Won't allow that.  I don't remember how to disable it. It was trivial.  I consider any automatic mounting a security failure, if I didn't specifically setup the mount.

---

### Post by Morbius1 on 2019-07-05
If I may offer a suggestion. Why not just create a Nautilus bookmark to the gvfs folder:

Go to /run/user/1000/gvfs in Nautilus > Select the Hamburger icon thingy on the top panel > then the "bookmark this location" tab thingy ( oh dear lord I hate what they've done to nautilus ). This will create a bookmark that will be visible on the side panel of Nautilus and your applications. You can even rename the bookmark to something other than "gvfs" if you desire.

Note: The bookmark resides at /home/your-user-name/.config/gtk-3.0/bookmarks and will look something like this for the gvfs bookmark:
```
file:///run/user/1000/gvfs gvfs
```
The second "gvfs" on that line is the Label of the bookmark and that can be changed.

---

