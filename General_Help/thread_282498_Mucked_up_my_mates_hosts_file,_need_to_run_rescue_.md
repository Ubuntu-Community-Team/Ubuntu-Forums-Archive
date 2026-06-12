---
title: "Mucked up my mates hosts file, need to run rescue CD to fix but can't"
date: 2006-10-22
forum: General Help
---

### Post by Sarisar on 2006-10-22
OK, so bear with me here.  I converted a mate onto Ubuntu (yay) and was trying to update his /etc/hosts file to include one of those lists that blocks ads and stuff.  Anyway I screwed up and overwrote the original one and didn't add it on to the bottom as I meant to.  Didn't realise until the following day when I tried to reboot and it complained about not finding host.

So now SUDO doesn't run because it can't find the 127.0.0.1 <compname> line (er.. gethostbyname() I think).  So no big deal, I can boot into the 'single user' mode is it (where you run as root) and simply nano /etc/hosts to fix this.

Problem is he isn't using grub... at least not the grub menu I get, so there is no option to do the single root boot thingy.  So I read up on here about using the live CD to run 'rescue' and get the same thing.  Unfortunately I had to leave (was due at my parents for food) but I left instructions (he's good with computers so he can do this).

Problem now is that he gets an error when trying to run the rescue disk.  Apparently "kernel panic-not syncing VFX Unable to mount root fs on unknown-block (8,1)" he said, although I found he probably meant VFS.

Searching the forums came up with the problem being with some libraries so I got him to download the new live CD (which was updated Aug 06 so should have the updated files) but still no joy.

Can anyone help me fix my mates PC?

---

### Post by CatKiller on 2006-10-22
All your friend needed to do was (from the live cd)
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/hda1 /mnt/ubuntu
sudo nano /mnt/ubuntu/etc/hosts
sudo shutdown -r now
```

You'll probably need to post more information about what your friend **actually** did to see if anyone else has come across the same thing. I haven't.

---

### Post by Sarisar on 2006-10-23
yay!  Well he said mnt should have been mount, but basically I cut and pasted your reply to him in an email and he fixed it from that :)

Thank you :)

---

### Post by CatKiller on 2006-10-23
I'm glad he got it working again.

---

