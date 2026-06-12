---
title: "setting azureus as default in firefox"
date: 2007-05-20
forum: General Help
---

### Post by jewishj on 2007-05-20
I have looked on the forums and haven't been able to find an answer.  I am trying to set azureus to be the default bit torrent handler in firefox.  When I click on a torrent file, I can either save it or open with... but the only open with option is the default gnome bittorrent or "other".  Obviously, I can set azureus by choosing other and finding it.. but I cannot find the azureus binary or whatever I would need to find to set it.  Does anyone know where it is installed to?  I used synaptic to install it.

Thanks

---

### Post by x64Jimbo on 2007-05-20
I have a workaround that you may find acceptable. I have Azureus set to monitor a directory on my machine and to automatically start downloading any .torrent file that it finds there. Then I just save all my .torrents there, and it's taken care of. It's really nice because I can use gFTP to initiate an SCP session with my desktop computer from anywhere, then drag over several .torrent files to that directory, and it automatically starts them while I'm away from home.

---

### Post by jewishj on 2007-05-22
I found it.  The path was /usr/bin/azureus

thanks

---

### Post by spartan777 on 2007-05-30
i tried associating /usr/bin/azureus as the handler for .torrent files in firefox, but when i try making use of it, azureus will lanch, but doesn't start downloading anything.

---

### Post by mlc on 2007-06-02
Jimbo,

I saw your post about setting Azureus to load torrents from a folder.  I've set the options in Azureus but it's not loading the torrents.  Is there something special?

Thanks

---

### Post by x64Jimbo on 2007-06-02
> **mlc said:**
> Jimbo,

I saw your post about setting Azureus to load torrents from a folder.  I've set the options in Azureus but it's not loading the torrents.  Is there something special?

Thanks

Tools > Options > Files > Torrents - Import new .torrents automatically
Fill in the correct location in the blank provided. You may need to hit the save button and restart azureus after that. You might also need to set the default save location so that they start downloading automatically and don't wait for your input.

---

### Post by badtlc on 2007-06-26
> **spartan777 said:**
> i tried associating /usr/bin/azureus as the handler for .torrent files in firefox, but when i try making use of it, azureus will lanch, but doesn't start downloading anything.

I'm having the exact same problem.

---

### Post by x64Jimbo on 2007-06-29
> **badtlc said:**
> I'm having the exact same problem.
Try having Azureus already running. You can start it with your session.

---

