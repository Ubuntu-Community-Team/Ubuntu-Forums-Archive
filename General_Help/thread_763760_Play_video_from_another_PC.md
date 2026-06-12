---
title: "Play video from another PC"
date: 2008-04-23
forum: General Help
---

### Post by sujoy on 2008-04-23
i want my laptop to connect to the desktop and play videos (songs,movies, etc), since thats where the bigger HDD is along with all of my collections.

now other than mounting the filesystem, is it possible to have the media from a particular directory or a number of directories to be streamed to my laptop ( or for that matter, any machine)?

if yes, then how do i set it up? also if there is an option then please suggest a lightweight app, thank you :)

---

### Post by notwen on 2008-04-23
Any reason you're not wanting to avoid mounting?  I do exactly what you're wanting by mounting my file server's HDDs via NFS on my laptop.

You could use a uPnP server like [uShare]("http://ushare.geexbox.org/") and then connect using VLC to stream via [this patch]("http://forum.videolan.org/viewtopic.php?t=2570").  I personally use uShare to stream videos to my Xbox 360.  I have not used VLC to stream via uPnP server, but it looks easy enough.  Perhaps you could look into this option.

---

### Post by ryanhaigh on 2008-04-23
While some applications in ubuntu fail to play movies over an samba share (not mounted samba just browsing the network and open a file) I have had good success using totem, the default movie player (it also plays music)

---

### Post by sujoy on 2008-04-23
the point is that i want to set up a similar thing in our hostel. (i didnt mention this before as i thought it would complicate my question).

now i cannot possibly mount over 300 HDDs!! so if we all could set up our PCs to stream media to a particular port(or i dont know what), and then use a client application to connect to any of those PCs and watch the content being offered, it would be great.

---

### Post by ryanhaigh on 2008-04-23
Well thats significantly more complex than I thought you were talking about. Do you want these streams to be on demand or just streamed like a tv show.

Perhaps you could use something like miro internally, setup a intranet site with 'channel' listings showing whats playing based on the same rss feed used miro. I don't know much about this but this link could help: [https://www.getmiro.com/create/](https://www.getmiro.com/create/)

This does sound like an interesting project, keep us updated!

This may also be useful: [http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/](http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/)
and you may want to have a look in synaptic...for example I found flumotion which sounds interesting as well as some other video streaming capable applications.

---

### Post by notwen on 2008-04-23
> now i cannot possibly mount over 300 HDDs!! so if we all could set up our PCs to stream media to a particular port(or i dont know what), and then use a client application to connect to any of those PCs and watch the content being offered, it would be great.

I'm guessing these 300 HDDs would be per room?  

You would only be mounting the server's media on each machine and you can have this done at startup by editing your /etc/fstab.  Getting the media to each room will not be the issue here, but if you're streaming media to each of these simultaneously, I would be more concerned w/ the internal network speeds.

---

### Post by sujoy on 2008-04-23
> **notwen said:**
> I'm guessing these 300 HDDs would be per room?  

You would only be mounting the server's media on each machine and you can have this done at startup by editing your /etc/fstab.  Getting the media to each room will not be the issue here, but if you're streaming media to each of these simultaneously, I would be more concerned w/ the internal network speeds.

well the network speed is standard wired LAN speed (100Mbps), now i was thinking of something more to the tune of MPD, wherein, each server PC could just stream their media database, and the client PC could just get access to all the database and then select which file he would like to see.

now i never done something so complex, so i am just trying to achieve the same thing in my home and take it up from there.

---

### Post by notwen on 2008-04-24
I'm not familiar w/ what you're wanting to do, but I would stick w/ NFS.  It is the easiest and you can have the client machines mount all of the server shares as read-only on boot and they're all set.    As far as what you're describing that is getting a bit beyond my knowledge.  Best of luck w/ this and be sure to post back and let us know what you try and conclude.  =]

---

### Post by rsay on 2008-04-24
I think mythbuntu automatically sets up a upnp media server that might meet your needs with very little hassle. I'm not sure if it would scale to 300 users though.

---

### Post by natrixgli on 2008-04-24
I was also going to suggest using MythTV. I had Vista on my laptop for a while and it detected the MythTV box as a uPnP media server and could play TV recordings, music, and videos.  I'm sure Mac / Linux would follow suit.


-n8

---

