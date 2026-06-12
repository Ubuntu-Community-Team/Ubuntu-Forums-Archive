---
title: "reinstalling grub"
date: 2016-02-21
forum: General Help
---

### Post by jakelong00 on 2016-02-21
I had ubuntu and windows 7 installed on my system. I wanted to install windows 10 on the system so I formatted the windows 7 drive and performed a clean installation.
At this point my system had ubuntu and windows 10 on it and I could boot only into windows. So I tried to install grub on the partition with ubuntu on it, through live cd , but couldn't do so.

Whenever i tried to mount the partition with ubuntu on it via:

sudo mount /dev/sda6/mnt (sda6 has ubuntu)
 
the terminal said:

couldn't find the path in etc/fstab (or something like this ,can't remember exactly)


then I simply ran:

sudo grub-install /dev/sda6

After this when I rebooted the pc, I got the (which I think is) grub rescue terminal with

"grub>"
prompt. At this prompt when I ran:

ls, it said
Error 27: unrecognized command

root (hd0,6)
it again gave an error

Now since I couldn't boot into any of the OS, I installed windows again.
How can I install the grub menu again so that I can once again choose which OS to boot into it?

Thanks

---

### Post by claracc on 2016-02-21
I recommend you follow a guide to install ubuntu alongside windows 10, I have found this: [http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html) . Process is clear and weel explained.

---

### Post by claracc on 2016-02-21
I think, this link : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) can be useful too.

---

### Post by jakelong00 on 2016-02-21
in BIOS Mode my PC says "Legacy"

---

### Post by ajgreeny on 2016-02-21
To  see what is really going on with this machine go to Boot-Repair in my signature below, follow the instructions to run the "Boot-repair" script and then post back here the pastebin link it gives you.

Do not blindly accept the default repair option for the moment; let us see everything first.

---

### Post by jakelong00 on 2016-02-21
> **ajgreeny said:**
> To  see what is really going on with this machine go to Boot-Repair in my signature below, follow the instructions to run the "Boot-repair" script and then post back here the pastebin link it gives you.

Do not blindly accept the default repair option for the moment; let us see everything first.


Thanks for the suggestion. It worked.
Now I have my OS selection menu back.:p

---

