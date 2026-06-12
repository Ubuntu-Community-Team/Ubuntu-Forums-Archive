---
title: "Broke sudo command while chown-ing"
date: 2018-04-07
forum: General Help
---

### Post by guydoodles on 2018-04-07
Uhm... So I was messing around with OpenBVE, and I needed to put some files into a folder that was owned by root. I did it the stupid way, not knowing what lied ahead. I typed:
```
sudo chown -hR gabriel /usr
```
It was taking a while so I quit the terminal and reopened it. This time I typed:
```
sudo chown -v -hR gabriel /usr
```
so that I could see what it was doing. Stupid, stupid, stupid...

Now I'm getting:
```
sudo: /usr/bin/sudo must be owned by uid 0 and have the setid bit set
```

How do I fix this?

---

### Post by HermanAB on 2018-04-08
Err... It may be time to test your backups and re-install.

After a screw-up of a system directory like that, you may find that the system will die slowly.  Over a period of time, more and more things will stop working and after a reboot, it may not come back up.

---

### Post by cruzer001 on 2018-04-08
Have a look here

[https://askubuntu.com/questions/452860/usr-bin-sudo-must-be-owned-by-uid-0-and-have-the-setuid-bit-set](https://askubuntu.com/questions/452860/usr-bin-sudo-must-be-owned-by-uid-0-and-have-the-setuid-bit-set)

---

### Post by jamesisin on 2018-04-08
Hmmm... not sure if /usr is supposed to be entirely owned by root.  If it is, then you ought to be able to log in using a live CD and fix that folder ownership recursively (more or less, just like you did to break it).  If /usr is not supposed to be owned entirely by root, then it gets more complicated (because you'd have to sort out who was supposed to own what) and you're likely better off rebuilding (though you can preserve your /home directories).

---

### Post by Impavidus on 2018-04-09
Just a quick check on my system (Xubuntu 17.10 with not too many applications installed)... It seems that /usr/bin/at, which is owned by deamon, is the only file or directory in /usr that's not owned by root, but that could be different on your system. You may be able to fix this. Recursively change ownership of everything in /usr to root, than change ownership of /usr/bin/at to deamon. You can use a live disk, but I think this will also work from recovery mode -> drop to root shell.

I can't guarantee it will work. The only way certain to work is reinstalling.

---

### Post by guydoodles on 2018-04-09
Craaaap... That backup setup dialog popped up once, but I just ignored it. Lesson learned, I guess. I'll try using recovery mode or a live CD (if I can find where I put it) to put it back to normal. Thanks for all your help!

---

