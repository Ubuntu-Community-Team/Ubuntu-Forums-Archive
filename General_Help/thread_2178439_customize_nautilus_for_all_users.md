---
title: "customize nautilus for all users"
date: 2013-10-03
forum: General Help
---

### Post by whatch on 2013-10-03
We are setting up dual boot Windows7/Ubuntu 12.04 computers.  Both systems will be joined to the domain via Likewise.  In Windows 7 we use group policies to redirect files to a central file server.  In Ubuntu is it is a bit more difficult.  With Nautilus we have figured out how users can navigate to their folder by going to: go > location > smb://fileserver/share/group/user, and they can then bookmark it, but it is not realistic to have users do this every time they sit at a different computer.  

How would I create a custom Nautilus launcher that is locked to the Unity sidebar, that would at least go to smb://fileserver/share?

Or, aside from purchasing something like Centrify, is there a better way to do this then with Nautilus?

Thanks.

---

### Post by theDaveTheRave on 2013-10-04
Whatch,

I would propose the following.

In each users home directory simply place a 'smbolic link' that can point directly to the correct location. You can then add this as a 'location' in favourites of nautilus.

How this should work....

If you have a 'networked folder' that folder will have a 'fully qualified name' such as
```

[COLOR="#0000FF"]Server.name.Ip.Address[/COLOR].[COLOR="#008000"]nameOfDrive[/COLOR]

```

When your linux box boots up you can mount this location either directly into the directory in the users home drive, or you can set up a special users, and mount it into this location, and have this shared to all other users.

what you need to research.

/dev/disk : is the default location of all devices that are locally available to a machine
mtab  and fatab :  will tell each system how to locate and mount directories / disks (these are config files located in the /etc/ directory
mount : this is the command to mount a file system (read HDD).

process:

read the [mount man pages]("http://linux.die.net/man/8/mount") for further info on using network locations to mount a file system
You may do well by reading the [ln man page]("http://linux.die.net/man/1/ln") also, make sure you understand the difference between hard and soft links.
Why? 
Simply if the user is using a laptop mostly they may want a copy of thier files available on this laptop, using a hard link will keep a copy of the same file in 2 location simultaneously, if it is deleted on one, it will remain on the other, if other users have a link to the same file, in effect it won't actually be deleted until ALL users have deleted the underlying file. ~ of course you may then have an issue of synchronisation, but it all depends on how you work.

Another idea may be to go for a 'cloud' type solution, I've not personaly used it, but [ownCloud.org]("http://ownCloud.org") docs make is sound like it should be quite easy to set up, there is even a package available, more info [in this thread on debian]("http://forums.debian.net/viewtopic.php?f=30&t=102803"), or own the [ownCloud forums here]("http://forum.owncloud.org/viewtopic.php?f=14&t=15670").

Then you can just add the owncloud server as a default favourite in the users browsers.

David

---

