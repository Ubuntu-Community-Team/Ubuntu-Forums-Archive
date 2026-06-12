---
title: "Seeding a torrent file with mldonkey"
date: 2006-12-12
forum: General Help
---

### Post by garlito on 2006-12-12
Hi all,

This is perhaps a too specific question about mldonkey, but I seem not be able to register in their forums, so I will try here: Does anyone know how to seed a non-previously download torrent file? That's to say, I've got the file.avi and the file.avi.torrent and I want mldonkey to seed it, but I didn't use mldonkey to  obtain neither of them.

I've tried to put the file in the incoming/files directory and the torrent in torrents/seeded, but it doesn't work, the torrent is quickly removed.

Please any clue?

---

### Post by bruenig on 2006-12-12
On normal bittorrent clients, what you would do is download the torrent file, open it with the client and then when it asks you where to save the file, save it to the same spot that the completed file in. It would then check your file, realize that you already have it and seed. 

I realize this is supposed to be some super client that has a whole bunch of protocols so it may be a little different, perhaps forcing you to put all your downloads in one folder to be compatible with other protocols. Just make sure that you have the file in the same place that you assign the client to save to.

Also, just because you have the same file does not necessarily mean it is the same torrent. Somebody could have created another torrent from that file. If that is the case, the torrent could very well not work and might have you download the file again.

---

### Post by garlito on 2006-12-13
Thanks bruening, but it works as it is supposed to work. I just had an incorrect name for the avi file, not matching the one in the torrent file (it was file.avi.avi, I hate that feature of nautilus of keeping the extension when rename :))

So, it is simple after all :)

---

