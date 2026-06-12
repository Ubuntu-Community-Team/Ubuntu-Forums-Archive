---
title: "Changing the default torrent programme"
date: 2008-04-27
forum: General Help
---

### Post by djrobthaman on 2008-04-27
Hi,

I was just wondering if anyone knows how to change the programme that opens torrent files by default.  More specifically, how do I make deluge the default programme that will show up in the firefox download pop-up.

Thanks

---

### Post by ibuclaw on 2008-04-27
When the download window pops-up.

Select "Open with Other"
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67612&stc=1&d=1209336445[/IMG]

Then type in the location of deluge.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67611&stc=1&d=1209336445[/IMG]

And finally check the box which tells FireFox to do this automatically from now on.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=67613&stc=1&d=1209336445[/IMG]


If the case is that you've already set Transmission as the automatic one, then go into "**Edit>Preferences**" and you can change it under the "**Applications"** tab.

Regards
Iain

---

### Post by djrobthaman on 2008-04-27
My main problem was I wasn't sure of its location.  In gutsy when I changed the system default to deluge it showed up in firefox, but not this time.

Thanks

---

### Post by airtonix on 2008-10-10
to find out where files are located : 

you can query the apt-get/dpkg databse : 
```
dpkg -l deluge
```

or you can query the file location database : 
```
locate deluge
```

can even use grep in both those cases.
```
locate deluge | grep /bin
```
```
dpkg -l deluge | grep /bin
```

---

### Post by scouser73 on 2008-10-10
What you can do is go to where you have saved the torrent file, then right click on the torrent file, select **Properites** then click the **Open With** tab and here you can choose the torrent client you wish to open torrents up from now on.

---

### Post by hyper_ch on 2008-10-10
you don't have to enter the full path (/usr/bin/deluge); you can just enter "deluge"

---

