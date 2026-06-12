---
title: "Desperate - can't log in gnome2_private: operation not permitted"
date: 2007-05-16
forum: General Help
---

### Post by cshelswell on 2007-05-16
Hi i'm having a real problem logging in. Yesterday i set up Samba to file share with a vmware XP installation. I eventually got this working but ended up with "$HOME/.dmrc file has incorrect permissions and is being
ignored"

So i followed a post on the forums here and did this:

sudo chmod 644 .dmrc
sudo chown username .dmrc
sudo chmod 755 /home/username
sudo chown username /home/username

however now i can't log in at all and /.xsession-errors is producing

**could not set mode 0700 on private per-user gnome configuration directory '/home/cshelswell/.gnome2_private/': operation not permitted**

I've tried chmod 700 .gnome2_private but get the same message. 

Any help to get in would be fantastic i'm totally stuck

Thanks

---

### Post by cshelswell on 2007-05-16
Managed to solve it 

found this on a german forum

chown -R username /home/username

there was a smiley face on the next reply so i went for it.

Seems to have worked
cheers

---

### Post by JunCTionS on 2008-01-19
Thank you :)
my Firefox didn't want to start and I got sort of the same error in konsole (kubuntu user)
probably had something to do with the fact that I restored my home folder from a backup I did as sudo and later on did a chmod -R 777 (that only allows everyone to read and write but doesn't change the superuser as the owner).

for some strange reason it worked with no problem until an apparent random moment that it needed "have" ownership.

anyways... good method on the smiley face thing :P

I want to add a thanks to cshelswell but don't know how. help out if you can.

---

