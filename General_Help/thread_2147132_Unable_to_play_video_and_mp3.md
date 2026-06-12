---
title: "Unable to play video and mp3"
date: 2013-05-20
forum: General Help
---

### Post by Tjkhan on 2013-05-20
I tried VLC, KM player and Movie player as well. No of them work.


Movie player shows error like below
[IMG]http://i1278.photobucket.com/albums/y504/tjkhan1/error_zpscd061200.png[/IMG]

VLC and KM player do nothing. Whats the solution?

Thank you.

---

### Post by Sugiura Ayano on 2013-05-21
Check this out:
[http://askubuntu.com/questions/166311/cannot-play-avi-or-mp4-file-in-both-movie-player-and-vlc](http://askubuntu.com/questions/166311/cannot-play-avi-or-mp4-file-in-both-movie-player-and-vlc)

My first guess was missing codecs, but VLC comes packaged with them.

---

### Post by monkeybrain2012 on 2013-05-21
Try "sudo apt-get ubuntu-restricted-extras" if it is missing codecs

If you downloaded the file from torrent like the guy in Sugiura Ayano's link  then chances are it may be a fake torrent (people put this things up for phising or something), especially if you see a lot of seeds but no comment on the torrent site.

---

### Post by Tjkhan on 2013-05-21
> **monkeybrain2012 said:**
> Try "sudo apt-get ubuntu-restricted-extras" if it is missing codecs

If you downloaded the file from torrent like the guy in Sugiura Ayano's link  then chances are it may be a fake torrent (people put this things up for phising or something), especially if you see a lot of seeds but no comment on the torrent site.

i didnt download from torrent. i downloaded from ubuntu software centre. But why I use "Movie Player" or all mp3. any solution?

---

### Post by helixo on 2013-05-21
download vlc player form the software center . . . .  it can prove to be a one stop solution for all such problems :) . . . if you cannot download vlc , maybe the problem is something different.. . .

---

### Post by mastablasta on 2013-05-21
> **helixo said:**
> download vlc player form the software center . . . . it can prove to be a one stop solution for all such problems :) . . . if you cannot download vlc , maybe the problem is something different.. . .


OP is already using VLC.

To the OP - install ubutnu restricted extras package found in software center.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

