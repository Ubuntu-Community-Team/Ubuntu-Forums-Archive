---
title: "Unable to mount CD"
date: 2024-10-14
forum: General Help
---

### Post by satimis on 2024-10-14
Hi all,

I tried to mount a music CD on terminal running
```

$ sudo mount /dev/sr0 /media/satimis/E0C8B186C8B15C0A/
mount: /media/satimis/E0C8B186C8B15C0A: can't read superblock on /dev/sr0.

```
but failed.

The cd can be played on cd player without problem.

I haven't used the CD Rom for long time.  Would it be its problem?

Please help.  Thanks

Regards

---

### Post by Holger_Gehrke on 2024-10-14
Audio CD doesn't have a file system, it just has a TOC (table of contents) which tells a player how many tracks there are and where they begin. What you see in the GUI / the file manager is not a real file system, it's a lot of trickery that involves GIO (Gnome Input/Output), gvfs (Gnome Virtual File System), and gvfsd-cdda (a helper for the gvfsd background process that handles CD Digital Audio). If all of that works as it should, you end up with the content of  Audio CD accessible as a set of .wav files in /run/user/'your numeric userid'/gvfs/cdda\:host\='device name' - e.g. /run/user/1000/gvfs/cdda\:host\=sr0/.

If it doesn't work automatically, you can try
```

gio mount cdda://sr0/

```

Holger

---

### Post by ActionParsnip on 2024-10-14
Audio CDs aren't data, so not mountable

---

### Post by satimis on 2024-10-14
> **Holger_Gehrke said:**
> Audio CD doesn't have a file system, it just has a TOC (table of contents) which tells a player how many tracks there are and where they begin. What you see in the GUI / the file manager is not a real file system, it's a lot of trickery that involves GIO (Gnome Input/Output), gvfs (Gnome Virtual File System), and gvfsd-cdda (a helper for the gvfsd background process that handles CD Digital Audio). If all of that works as it should, you end up with the content of  Audio CD accessible as a set of .wav files in /run/user/'your numeric userid'/gvfs/cdda\:host\='device name' - e.g. /run/user/1000/gvfs/cdda\:host\=sr0/.

If it doesn't work automatically, you can try
```

gio mount cdda://sr0/

```

Holger_Gehrke
Hi Holger,

Lot of thanks for your advice.

This is a DVD writer.  I haven't used it for quite long time.

Actually I tried reading data burnt on a CD-RW.  They are old data.  I tried to mount it running;

$ sudo mount /dev/sr0 /media/satimis/E0C8B186C8B15C0A/
[sudo] password for satimis: ```

mount: /media/satimis/E0C8B186C8B15C0A: no medium found on /dev/sr0.

```
I thought that the CD RW disc is damaged unable to mount therefore I tested a music CD.

The strange thing is "VLC media player" unable to play the music CD
Start VLC
Media -> Open Disc
(select) Audio CD
Disc device [/dev/sr0 ]
Track [1]
-> Play

No response.  It is very strange to me.  Previously it worked.

Regards

---

### Post by satimis on 2024-10-14
> **ActionParsnip said:**
> Audio CDs aren't data, so not mountable
Hi,

Thanks for your advice.

Regards

---

