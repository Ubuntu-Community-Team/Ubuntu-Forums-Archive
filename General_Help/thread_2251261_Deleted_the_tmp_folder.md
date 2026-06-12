---
title: "Deleted the tmp folder"
date: 2014-11-03
forum: General Help
---

### Post by minerbog on 2014-11-03
Hi All, (Ubuntu 14.04LTS)

I hope this is in the right place, I couldn't find the "OMG I've just delete my tmp folder and screwed my system" forum!!

So, basiclly its that, I thought I was in my home folder but wasn't and delete the tmp folder from the root "/". The only one of the four files I remember started with X11. I have no idea what I have deleted!

Now the terminal just closed randomly when I try to run any command. Non of my browsers work. When I even try to go into the full terminal "Ctrl+Alt+F5" or 6 or 4, I get the following just randomly appearing.
```
[768.799054]hda-codec:out of range cmd 2:5:707:ffffffbf
```
The number in the square brackets climbs constantly so I assume this is a time or process counter and the number 2 (before the 5) changes to either 0,1 or 3.

Please help guys, I'm lost!!

Gavin.

---

### Post by nerdtron on 2014-11-03
If it is just the /tmp folder I assume you can still restore it since there are no important files in there.
You can try booting into a Live USB and then mount you Ubuntu partition.
Now you can try to create the tmp folder. Remember the permissions of the /tmp folder is 777 plus the sticky bit.
```
chmod 777 /media/ubuntu-hd/tmp
chmod +t /media/ubuntu-hd/tmp
```

At least it's worth a try.

---

### Post by Impavidus on 2014-11-03
/tmp contains nothing important and is automatically wiped on reboot. From a live disk you can recreate it and set the correct permissions. It must be owned by root and have full permissions and the sticky bit.```
sudo mkdir /media/ubuntu-hd/tmp
sudo chmod 1777 /media/ubuntu-hd/tmp
```This is more or less the same as nerdtron suggests. Then, of course, reboot. With some luck it may work.

---

### Post by minerbog on 2014-11-03
Thanks guys, all up and running again!!

Stupid thing is, I did create a new tmp folder using sudo. I just didn't chmod 777 it!!!

DOH!

---

