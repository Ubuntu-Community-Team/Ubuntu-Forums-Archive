---
title: "mp3 will not play in ubuntu Hardy 8.04. Just stays at 0:00 seconds"
date: 2013-05-13
forum: General Help
---

### Post by 777funk on 2013-05-13
I don't know why this could be. It opens the track but remains at 0:00.

---

### Post by prodigy_ on 2013-05-13
8.04 is no longer supported. You should upgrade. Or install a current version of some other distro.

---

### Post by 777funk on 2013-05-13
true but I'm afraid my old P4 laptop won't appreciate Ubuntu V12 in the speed dept. That's why I installed 8.04. I like 12.04 much better so I wish I could!!!

---

### Post by ajgreeny on 2013-05-13
Try xubuntu 12.04!

---

### Post by ipeters61 on 2013-05-13
> **777funk said:**
> true but I'm afraid my old P4 laptop won't appreciate Ubuntu V12 in the speed dept. That's why I installed 8.04. I like 12.04 much better so I wish I could!!!

I use Xubuntu 13.04 on my Pentium 4 desktop (2 GHz, no less, with 1.25 GB RAM) and it runs nicely.  I found that using an ext2 file system was really helpful in improving speed (but it slows down the boot because the system always insists on running a file system check).

In that case, you can install the GStreamer plugins (I think GStreamer Plugins Ugly) in the software center and MP3 files should play.

---

### Post by Dennis N on 2013-05-13
> **777funk said:**
> I don't know why this could be. It opens the track but remains at 0:00.

Are we talking about one mp3 file, or every mp3 file? If one file, it could be just be corrupted.

---

### Post by 777funk on 2013-05-13
thanks for the replies everyone. AAnd Dennis N, it is every mp3. None will play.

---

### Post by tgalati4 on 2013-05-13
Some mp3's have small pictures (album art) embedded in them.  That may trip up the older mp3 players.  Look at the files in *easytag* and delete the picture and save the file.  Then try playing it.

Open a terminal:

```
mplayer mp3filethatIamhavingtroublewithonaseriouslyoldubuntureleasethatIamhappywith.mp3
```

Post any useful output.

---

### Post by Moose on 2013-05-13
> **tgalati4 said:**
> 
```
mplayer mp3filethatIamhavingtroublewithonaseriouslyoldubuntureleasethatIamhappywith.mp3
```

Post any useful output.

I'll admit, I found this pretty damn funny. XD

---

### Post by Dennis N on 2013-05-13
> **777funk said:**
> thanks for the replies everyone. AAnd Dennis N, it is every mp3. None will play.

Can you play other music formats, such as .ogg?
Have you been able to play mp3 files previously on this system?
What audio player are you using?

---

### Post by 777funk on 2013-05-14
Ok, I just did the following:

> 
sudo apt-get install xubuntu-desktop
sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove


I then restarted and the login screen said XUBUNTU but after that it looked just like regular UBUNTU 8.04. Is this normal? It was like everything visually at least appeared as if I hadn't done anything.

Next I upgraded to 10.04 and that looks much different. 12.04 is next. But I want to make sure I'm on Xubuntu.

---

### Post by Impavidus on 2013-05-14
Maybe a clean install would be better, but as you already did one upgrade, just continue and see how it works.

To completely convert to Xubuntu after upgrading to 12.04, see [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce) and [http://www.psychocats.net/ubuntu/purexubuntuprecise](http://www.psychocats.net/ubuntu/purexubuntuprecise)

---

