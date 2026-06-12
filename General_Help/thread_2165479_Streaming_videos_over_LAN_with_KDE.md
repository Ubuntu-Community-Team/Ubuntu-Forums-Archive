---
title: "Streaming videos over LAN with KDE?"
date: 2013-08-05
forum: General Help
---

### Post by Roasted on 2013-08-05
Am I missing something, or is this a feature still missing in KDE? I fired up Kubuntu 13.04 and PPA'd in KDE 4.10 and started to tinker around. KDE has all sorts of great features and I enjoy it tremendously, but continual half baked edges just continue to be a frustration. I went into system settings, added my username and password for my login with my Samba server and then went to town. With the built in Dragon Player, I get nothing. It errors out. VLC, same deal. There is some hope if I go into VLC's advanced preferences and find the smb protocol and put in my login there, but it begs the question, why must I do that? Am I missing a critical step or is it safe to say that after all of these years, out of the box video streaming from a LAN resource is still a missing commodity?

---

### Post by Erik1984 on 2013-08-05
What if you access the samba share from Dolphin and then try to open the video file in Dragon Player?

---

### Post by SeijiSensei on 2013-08-05
Video streaming works flawlessly if you use NFS to share files rather than Samba.  I stream 720p files over wifi from my server with NFS all the time.  

With Samba, most players first copy the remote file to the local machine then play the local copy.  I don't know why they don't play the networked copy.  

You can use both NFS and Samba on the same server so you can support Windows users as well.

---

### Post by Roasted on 2013-08-05
> **SeijiSensei said:**
> Video streaming works flawlessly if you use NFS to share files rather than Samba.  I stream 720p files over wifi from my server with NFS all the time.  

With Samba, most players first copy the remote file to the local machine then play the local copy.  I don't know why they don't play the networked copy.  

You can use both NFS and Samba on the same server so you can support Windows users as well.

I've been down the NFS route. It's not a setup that I particularly enjoy. To be quite frank, user based authentication that works flawlessly on any OS I have (I do it a bit of the 3 main contenders) is really a no brainer. It's just incredibly disappointing to see KDE struggling with this, even today, whereas every other DE I use (which are admittedly mostly GTK based, taking advantage of the awesomeness behind GVFS) seem to have no issue with it at all. Due to this I can't help but to think, there's GOT to be a way, and I'm clearly just missing it...

---

### Post by chris2kari on 2013-08-06
Install smb4k & use it to mount SMB shares. 
This works beautifully. 

Likewise in the Gnome environment Gigolo. 

Chris

---

### Post by Roasted on 2013-08-06
Thanks. I'll look into it. I just thought that this sort of functionality should be available by default. In other news I reported a bug for it that got marked as a duplicate. I checked out the original bug and it seems its been a work in progress for three years now. Sigh... :-( 

My 2c - I think I'll be sticking to Gnome. (For reasons beyond this particular issue)

---

