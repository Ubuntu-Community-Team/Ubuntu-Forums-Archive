---
title: "Transmission - Download to external hard drive // Ubuntu Server"
date: 2013-06-05
forum: General Help
---

### Post by emilnygaardfrisk on 2013-06-05
I have just setup a ubuntu server, on this server i installed transmission so i can download torrents from the web-ui. Transmission works great! Today i got the idea that i wanted to download to an external hard drive. I mounted the hard drive and set transmission to download to the dedicated folder i made on the external drive. But of course transmission does not have permissions to write to the external drive. 

How can i solve this? Can i run transmission as "root" user which should have permissions?

I hope that you can help me. Thanks a lot!

---

### Post by greatsirkain on 2013-06-05
chown the drive
more details here:
[http://ubuntuforums.org/showthread.php?t=1140523](http://ubuntuforums.org/showthread.php?t=1140523)

---

### Post by The Cog on 2013-06-05
How are you mounting the drive? I would expect that if you do it with nautilus (places in the sidebar if I remember), it should mount owned by you. If you use the mount command under sudo, you will need to use an option to set the owner/user - "mount -o uid=1000 ..." or whatever your user id is.

I would  not recommend running transmission as root.

---

