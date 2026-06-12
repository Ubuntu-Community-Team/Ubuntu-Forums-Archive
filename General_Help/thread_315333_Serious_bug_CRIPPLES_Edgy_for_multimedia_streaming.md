---
title: "Serious bug CRIPPLES Edgy for multimedia streaming"
date: 2006-12-09
forum: General Help
---

### Post by nexu56 on 2006-12-09
I'm loving Edgy to bits except for one huge, showstopper bug. If you use nautilus to connect to a remote server in the regular, Gnome-y way (Places -> Connect To Server), the files in this network folder will no longer allow you to play multimedia -- music, movies, etc. The error is "Could not read from resource".

The bug is listed in these forums in the ["Known bugs in Edgy" thread, ]("http://www.ubuntuforums.org/showthread.php?t=283364")however the workaround provided ("dont use totem") is incorrect, the problem affects all non-gstreamer players I have found as well. I think this is because it [appears]("https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/60326") to be a [problem]("http://bugzilla.gnome.org/show_bug.cgi?id=351322") with [libgnomevfs.]("http://bugzilla.gnome.org/show_bug.cgi?id=359133")

This bug has been around since October, and given the impact I'm shocked it hasn't been fixed yet. ](*,) I'm sure storing all your music and video on a file server and streaming to your desktop is an extremely common thing to do... I'm not hassling the wonderful gnome people, but this really needs to be fixed URGENTLY -- simply look at the number of duplicate bugs in both Gnome's bugzilla and launchpad.

Which brings me to the point of this post... is there an Ubuntu Hero out there who can step up and help us noobs? Can anyone give us:

1) Confirmation that devs are aware of the problem and there is some timeline to get it fixed?

2) A real workaround (step by step instructions on how to downgrade libgnomevfs?)

I and many others would be extremely grateful!

---

### Post by yopnono on 2006-12-09
On my edgy I edited my smb-module.conf file in folder
```
/etc/gnome-vfs-2.0/modules
```
change
```
smb: [daemon] libsmb
```
to
```
smb: libsmb
```

---

### Post by nexu56 on 2006-12-09
Works perfectly... thanks!!

---

### Post by marcele on 2006-12-11
Thanks for this! Now I can play my mp3's in rhythmbox via smb:// !
**This should be sticky !!**

---

### Post by t0ljan on 2006-12-13
Works nice!
Thanks

---

### Post by Buck2348 on 2007-01-12
Great job!  I'm always tempted to ask:  How did you know what to do?  Anyway, this has fixed a bug that has bothered me ever since upgrading to edgy.  I don't stream music, but it was annoying to try to browse samba shares with nautilus because the wrong icon would often be displayed and when clicked on give an error message.  The bug has been documented in launchpad and fixed in Feisty, but like nexu 56 I wonder why such a simple fix has not been published or the problem fixed in an update.

Buck

---

### Post by yopnono on 2007-01-13
> **Buck2348 said:**
> Great job!  I'm always tempted to ask:  How did you know what to do?  Anyway, this has fixed a bug that has bothered me ever since upgrading to edgy.  I don't stream music, but it was annoying to try to browse samba shares with nautilus because the wrong icon would often be displayed and when clicked on give an error message.  The bug has been documented in launchpad and fixed in Feisty, but like nexu 56 I wonder why such a simple fix has not been published or the problem fixed in an update.

Buck

Search engines like google

---

### Post by Derspankster on 2007-01-13
Thanks so much - it does indeed work!  But, for me, only with Totem. XMMS still does not stream.  I'm so glad someone finally posted a fix. Thanks again.

---

### Post by Tomosaur on 2007-01-13
Please file a bug report on [http://launchpad.net](http://launchpad.net), the developers don't read these forums.

---

### Post by yopnono on 2007-01-13
> **Tomosaur said:**
> Please file a bug report on [http://launchpad.net](http://launchpad.net), the developers don't read these forums.

They know. Also the gnome devs since a long time

---

### Post by yopnono on 2007-01-13
> **yopnono said:**
> They know. Also the gnome devs since a long time

But whata... spam them to get focus on it :)

---

### Post by .tommie on 2007-01-15
Great, going to try this out!

---

### Post by g8m on 2007-01-19
Because of this bug I wrote a program and a scripted it into nautilus.
This allowed me to mount samba shares on a subfolder the old
fashioned way, smbmount //server/share mountpoint.

Never realized it was a bug. I just thought it was a shortcoming of the smb:
approach.

It gave me some insight in gtk and nautilus, but my approach 
was ofcourse wrong. A bug, not a feature.

---

### Post by Shatrat on 2007-01-19
Great workaround Yopnono.  I've been searching off and on for days and had though there was no way around it but to transfer the whole file and play it locally.

This really should be edited into the "Known Bugs" thread, I know there are quite a few threads concerning this bug on these forums and others and this is the first fix I've seen.

---

### Post by cracker on 2007-01-20
> **g8m said:**
> Because of this bug I wrote a program and a scripted it into nautilus.
This allowed me to mount samba shares on a subfolder the old
fashioned way, smbmount //server/share mountpoint.

Never realized it was a bug. I just thought it was a shortcoming of the smb:
approach.

It gave me some insight in gtk and nautilus, but my approach 
was ofcourse wrong. A bug, not a feature.

I was convinced of the exact same thing. For me, this problem has existed since I first started using Ubuntu, with 5.10. Thanks a ton for this info!

---

### Post by feest on 2007-01-20
> **yopnono said:**
> On my edgy I edited my smb-module.conf file in folder
```
/etc/gnome-vfs-2.0/modules
```
change
```
smb: [daemon] libsmb
```
to
```
smb: libsmb
```

th now i can finally enjoy tux' friends in happy feet using smb :)

---

### Post by jon schroeder on 2007-12-01
For Ubuntu 7.10:

Go to same directory: /etc/gnome-vfs-2.0/modules 

and edit: extra-modules.conf

or just  try gs-streamer instead of xine for totem.  gs-streamer totem plug-in works better for me when streaming media files across the local network.

---

