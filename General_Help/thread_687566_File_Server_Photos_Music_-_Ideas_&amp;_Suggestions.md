---
title: "File Server Photos Music - Ideas &amp; Suggestions"
date: 2008-02-04
forum: General Help
---

### Post by firebadger on 2008-02-04
I want to set up a file and print server for use at home and I'm looking for advice/thoughts before I get started.

All my home machines are currently Kubuntu and I'm not likely to start using Mac or (heaven forbid) Windows any time soon.

I want to share photos so that I have two folders one that I have rw access to but my wife only has r access and another that we both have rw to (for her photos).  We will both be using digikam to manage them.  I'm a little concerned that we may have problems if we both try to do this at the same time.

I want to share music (rw for me r only for others) and I want Amarok on remote machines to be able to add these network locations to their libraries.

I'm thinking of Samba as I know that I will have problems with SSH.  Amarok refuses to play remote files using ssh although it allows you to add them to the playlist.

Also any pointers on setting up as a print server.  I've not tried this yet and it may be surprisingly easy.

Anyway, any input very welcome.

---

### Post by stalker145 on 2008-02-04
> **firebadger said:**
> I want to share photos so that I have two folders one that I have rw access to but my wife only has r access and another that we both have rw to (for her photos).

I want to share music (rw for me r only for others) and I want Amarok on remote machines to be able to add these network locations to their libraries.

I haven't tried it yet since I'm the only one on my network, but shouldn't simple permissions take care of this?

---

### Post by firebadger on 2008-02-04
Yes I think so.  That's not really a specific concern, I was just giving some background so that anybody who has implemented something similar or has any other input would have a better idea of what I was trying to acheive.

I don't really have any specific issues that I aware of yet, I just want to see if anyone can think of any advice or gotchas that might be useful before I get started.

Thanks for replying though.

---

### Post by .nedberg on 2008-02-04
I use NFS for my music and images. It is very easy to set up, but digiKam does not work very good with it. I would recomend Samba for images.

I just installed a print server with ubuntu at work and it was also very easy. Plug in the printer, make it shared and there you are! I share it with Samba, so to keep things simple go the Samba way with all shares. Permisions will take care of the rw/ro bit.

---

