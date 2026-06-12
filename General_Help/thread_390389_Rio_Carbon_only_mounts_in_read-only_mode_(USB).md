---
title: "Rio Carbon only mounts in read-only mode (USB)"
date: 2007-03-21
forum: General Help
---

### Post by illiterate_light on 2007-03-21
I have a Rio Carbon mp3 player that I can only mount in read-only mode.  Running Dapper Drake 6.06.

I've tried automounting it, tried adding a line to fstab, tried rebooting with it plugged in/not plugged in, and no matter how it mounts, it's always read-only and I can't add/remove/modify anything.

Currently my fstab has this line:

/dev/sda1       /home/me/rio     vfat rw,defaults,umask=0000 0 0

Pretty sure I've tried other configurations, but for some reason this particular drive insists on mounting read-only.  Apparently other people have had the same problem, but I haven't seen a solution anywhere.  Any ideas?

---

### Post by tousman on 2007-05-26
Hi, 

I also have a RIO and I have found a way to make it "work" although it is not ideal because the files I copy from my RIO to my /home have Super User privileges, so I cannot rename, delete, ... via the GUI and needs to do everything from the terminal as a SU.

I do: 
sudo mount -t vfat /dev/sda1 /media/RIO

Hope it helps.
If someone could advise on how to mount the device so that I do not have to be a SU to copy paste to and from the RIO that would be great. If there is a way to add this device to the /etc/fstab so that it automount I would also be interested. 

Cheers

---

### Post by tousman on 2007-05-27
Well adding the device to the fstab helped. 
Now I can copy from the RIO to my /home and the file owner is the normal user, not root. 
I would still be interested to know how to automount... 
Cheers.

---

### Post by JackandJohn on 2008-01-30
Also note: some versions of Ubuntu will not easily allow a usb mass storage device to be read/write if it's damaged (Strangely, it will mount as read-only with no obvious errors)

I fought with one for a while before I learned that

---

