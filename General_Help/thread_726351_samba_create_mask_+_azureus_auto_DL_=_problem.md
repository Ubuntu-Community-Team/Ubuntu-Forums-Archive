---
title: "samba create mask + azureus auto DL = problem"
date: 2008-03-16
forum: General Help
---

### Post by Darth_tater on 2008-03-16
I have a headless box set up that is my bit torrent server.  Primarily, it acts as a tracker (I host some files for friends + family) but occasionally I will use it as a download box as well.  Since it is headless machine I use SAMBA to put torrents on a special file share that azureus periodically checks for new torrents.

My problems is this:
I can successfully access the share from windows and I can put torrents on the share, but the permissions are preventing azureus from loading the file.  I opened nautilus to the share and looked inside.  My torrent files were there  but the permissions were set so that ROOT was the owner and could r/w/x.  The problems is that azureus cant access these files… the permissions wont let it.

My question: 
In my smb.conf I need to specify the create mask so that the user that azureus runs under (me) can access the file.  What do I need to have it set to? 

As of now, it is 0700.  I do not fully understand the permissions scheme under linux but I know enough to realize that files are going to be made so that root is the only one who even knows they are there.  Help me fix this, please.

Thanks in advance for any and all help you can provide.

---

### Post by Darth_tater on 2008-03-18
i figured it out.

to do what i needed in accordance with the disk permissions i have i needed to specify a create mask of 0755

thanks though.

---

