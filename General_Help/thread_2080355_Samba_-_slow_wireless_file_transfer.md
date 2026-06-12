---
title: "Samba - slow wireless file transfer"
date: 2012-11-03
forum: General Help
---

### Post by chadwell on 2012-11-03
I have an laptop running 12.04 Ubuntu, which is acting as a dedicated NAS. I store all my photo and videos on it etc

I use Samba and smb.conf to share to other devices. I can access it and transfer photos etc from my phone and a windows 7 netbook. I get wireless transfer speeds of 2MB/sec on these devices.

I bought a new iPad and installed the paid app filebrowser - so I could access the NAS over wireless and copy files or view photos etc. But the transfer speeds are 100KB/sec.

No matter what file I transfer I get really slow speeds. I contacted the makers of file browser and they said it may be due to the packet size and there may be a way to change the packet size in the smb.conf.

I have searched and have not found anything. I read about the socket options somewhere, and I uncommented out the line and changed to the following:

socket options=TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

but this is in the MISC section of my SMB.conf - does it nee to be in global or does it not matter.

Any help appreciated

---

### Post by chadwell on 2012-11-04
Any ideas why this is slow, or where I could find some answers.

---

### Post by chadwell on 2012-11-05
Doesn't anyone have any missiles left?

---

### Post by chadwell on 2012-11-06
Just tried writing about 100 images (over 300MB worth) to the NAS drive from the iPad using filebrowser.

It took about 3 mins which is great and seems about right.  So the problem seems to be **reading** from the NAS?  Does this narrow the problem down any??

---

### Post by Izzard on 2013-01-03
Same problem here. 
No help.

---

### Post by BertN45 on 2013-01-03
With Windows and your phone you get 2 mbps both ways in file transfers. With the iPad you get nice speed sending photos from the iPad, but get terrible slow speeds receiving photos in your iPad. For me it clearly looks as an iPad problem, since both phone and Windows machine work without any problem.
The remark about the buffer size is not to the point, because also your other devices should have been suffering from those low speeds. Besides increasing the buffer size will not give a 20 times faster transfer.

I would try transfers from iPad to/from your Windows machine, if they are slow too, I would call/email Apple again. If it occurs with Windows too, they might pay somewhat more attention to your complaint.

I also would try it with larger files say 500MB. In that case you eliminate potential overheads with opening and closing many files.

---

