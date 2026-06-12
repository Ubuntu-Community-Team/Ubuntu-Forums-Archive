---
title: "Mounting an external hard drive to a different directory?"
date: 2014-07-22
forum: General Help
---

### Post by Camw22 on 2014-07-22
I have a problem. I recently upgraded to 14.04 yesterday from 12.04 (I know, i'm behind). All of my media is stored on an external hard drive, and with that media, a lot of VLC playlists. When I open any playlist VLC is flagging an error saying that it called for /media/1TB Hard Drive/ and could not find any of the videos on the playlist. I recently discovered that my external drive is now mounted on /media/cam/1TB Hard Drive/ . Is there possibly a way to change the automount back to /media/1TB Hard Drive/ so I do not have to go through hours of sorting out multiple playlists again?

---

### Post by slooksterpsv on 2014-07-22
You sure can, do the following - may want to get the dev ID first via df then do this:
```

sudo mkdir /media/1TB\ Hard\ Drive
sudo umount /media/cam/1TB\ Hard\ Drive
sudo mount /dev/sd*x#* /media/1TB\ Hard\ Drive/

```

Where x and # are the dev id of your hard drive. 

For my Windows partition it's this
```

/dev/sda4      597829628 472233788 125595840  79% /media/shawn/TI10675800F

```

If you always have the drive connected to the machine, you can add an fstab entry to have it automount to that directory. You can also make the above into a script and run it as a shortcut too.

---

### Post by Camw22 on 2014-07-22
Thank you so much, you sir have saved me tons of hair-pulling out! I thought I was doomed!

---

