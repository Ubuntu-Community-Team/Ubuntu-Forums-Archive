---
title: "Does ktorrent have a problem with mounted volumes?"
date: 2008-02-13
forum: General Help
---

### Post by paulkaye on 2008-02-13
Hiya - complete newbie here!

I'm running ubuntu on an old laptop and am shocked at how much faster and stable it is than Windows. The trouble is that the hard drive on the laptop is tiny and I'd like to set up ktorrent to use a mounted volume - I have a NAS on the network. I'm pretty sure I've mounted it correctly because if I go into /home/[me]/torrentmount, I see everything in the appropriate folder on the NAS. 

However, when I set this folder as the torrent folder in ktorrent and then try to download a torrent I get the error > Cannot create /home/[me]/torrentmount/[file to be downloaded]. No such file or directory. Ktorrent then quits.

Any suggestions as to why this is happening? I don't quite understand which 'level' the mount is on. Does everything apart from the OS see it as a regular directory? A friend was trying to explain that the GUI is distinct from the OS which, in principle, I understand but I would expect there to be a way to mount at the OS level, no?

Thanks in advance for your time!

Paul

---

### Post by p_quarles on 2008-02-13
What type of filesystem is the NAS using? Have you checked the permissions on the mounted volume? Are you able to drag-and-drop files into the mounted volume using your file manager?

---

### Post by paulkaye on 2008-02-13
It's the Freecom FSG and it uses a linux system (that's all I can tell you as that's all I understand!). See [here]("http://www.openfsg.com") for info.

I'm not at the machine now so can't test the permissions when the volume is mounted. However, if it's relevant, I know that I _can_ write to this folder when I access it manually through the network browser.

---

### Post by paulkaye on 2008-02-18
Shameless bump, I'm afraid!

---

### Post by p_quarles on 2008-02-18
Hard to say what the problem is without more information. If you could post the output of the following, someone might be able to spot the issue:
```
cat /etc/mtab
```
This will return basic information about all mounted filesystems. 

Then, check the permissions on the NAS:
```
ls -l /path/to/device
```

---

