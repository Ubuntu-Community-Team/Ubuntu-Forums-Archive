---
title: "I/O Buffer errors at the fsck"
date: 2006-11-02
forum: General Help
---

### Post by finferflu on 2006-11-02
Hi all,
I'm experiencing one of my usual weird problems...

This time, on my friend's laptop, I can't go past the automatic fsck (the one that comes up every 30 times you restart). It makes an error with I/O Buffer, and then it gives me a shell on which I am suggested to run fsck, but still I can't get away with that. The Hard Drive makes some really weird noises, and I/O Buffer errors fill the screen.

This is a brand new Hard Drive, bought about 3 weeks ago, I had to replace the old one because it made similar noises, but I couldn't even startup the system. 

The point is that everything worked fine until that fsck, and I would like to have my system back. I'm also willing to skip the fsck every 30 times if possible.. Could anybody help?

By the way, the laptop is a Toshiba A21m with Edgy Eft installed.

Thank you for your time!

---

### Post by mattme on 2006-11-03
Hum. Surely something is bad if you are getting those errors. I'd try completing fsck (filesystem check) at that shell..  a combination of the following options
fsck -f (force check)
fsck -p (automatic repair)
fsck -y (answer yes to everything)

whether fsck runs at boot is declared in /etc/fstab (filesystem tables). edit as root eg
sudoedit /etc/fstab
look around. each row corresponds to a device to be mounted. each row has format
device-to-be-mounted mount-point type options and then two separate digits. the first does something i can't remember. the second tells whether the partition should be checked ocassionally. 0 is disabled, 1 2 3 indicates the order. change them to zero..
(control o to save, control x is exit)

i'm not sure where the 1/30 interval is specified.

---

### Post by finferflu on 2006-11-03
Thank you very much for your exaustive answer. 
For the moment I've just disabled the fsck at boot. The system goes like a charm... I don't get what can be wrong.
Anyway, I'll try to run one of those commands from a shell after the login, and see what happens.

Thanks a lot!

---

