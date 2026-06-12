---
title: "can't login to desktop! I login and it returns to the login page again!"
date: 2006-11-25
forum: General Help
---

### Post by Isoss on 2006-11-25
Hello

I have edgy, and I was upgrading the system after I noticed 35 upgrades waiting for me in the update manager. it told me that some packages can't be installed unless I do a dist-upgrade! well I proceeded the upgrade anyway. atfer that I plugged a new DVD drive into my case (while the pc was turned on) and usually the system would mount it but it didin't, so I waited untill the upgrades are done, and when they were done it told me that some packages couldn't be installed .. anyway, I rebooted the system, and when I tried to login it returned to the login page again!! I noticed that when I do it takes me to a black shell with a flashing dash "-" in the top left corner then returns to login page again! 

this usually happens when something goes wrong with beryl or something related to xserver .. but I don't have beryl installed on this PC and I don't think I did anything related to vga or anything similar!

I tried to login to failsafe Gnome and failsafe terminal but same problem!

I hit ctrl+alt+1 to get a shell, I ran apt-get dist-upgrade and it download something but couldn't install everything and gave me an error that I have to run update or with --fix-missing, and so I obeyed it to no avail! 

xorg.conf look fine! and I don't remember I did anything nasty! 

How can I fix this? is there anyway that I can find out where the problem is?


any help will be appreciated!

---

### Post by xopher on 2006-11-25
Do you have any other users on the system?
If you have a root account, does it work to log in with it?

If it does - then we've narrowed down the problem to your gnome-session, which you might have to reset to get back your log in.

If not - then its harder to say what it is. What are the packages that were upgraded? And what packages gave you errors?

- Christoffer

---

### Post by Isoss on 2006-11-25
I don't have anyother user and don't have a root account! maybe it could work if I can create one in the shell. I jsut don't know how to create that.

I'll go chack again what are the ackages that are causing the problem!

it's really something bad there isn't a way to figure out what's broken in the system! I don't want to reinstall the system again! for me that's a whole day!

Thanks

---

